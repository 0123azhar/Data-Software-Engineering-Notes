2024-08-24 10:07
# Azure devops

### Complete Production-Ready YAML Pipeline for a Python Application

#### 1. **Pipeline Structure Overview**
This pipeline is structured to:
- **Build** the Python application.
- **Test** the application using unit tests.
- **Deploy** the application to a staging environment.
- **Require approval before deploying** to the production environment.
- **Deploy** the application to production after approval.

#### 2. **YAML Pipeline Example**

```yaml
# Trigger the pipeline when changes are made to the main branch
trigger:
  branches:
    include:
      - main

# Use the latest Ubuntu-based virtual machine image for the agent
pool:
  vmImage: 'ubuntu-latest'

# Define pipeline variables
variables:
  pythonVersion: '3.x'
  appName: 'my-python-app'
  azureSubscription: '<YourAzureSubscription>'

# Define stages of the pipeline
stages:
  # Build Stage
  - stage: Build
    jobs:
      - job: Build
        steps:
          # Step 1: Set up Python version
          - task: UsePythonVersion@0
            inputs:
              versionSpec: '$(pythonVersion)'
              addToPath: true

          # Step 2: Install dependencies
          - script: |
              python -m pip install --upgrade pip
              pip install -r requirements.txt
            displayName: 'Install dependencies'

          # Step 3: Lint the code (optional but recommended)
          - script: |
              pip install flake8
              flake8 .
            displayName: 'Lint the code'

          # Step 4: Run unit tests (as part of the build process)
          - script: |
              pip install pytest
              pytest
            displayName: 'Run unit tests'

          # Step 5: Package the application
          - script: |
              python setup.py sdist bdist_wheel
            displayName: 'Package the application'

          # Step 6: Publish the build artifacts
          - task: PublishBuildArtifacts@1
            inputs:
              PathtoPublish: 'dist'
              ArtifactName: 'python-package'
              publishLocation: 'Container'

  # Staging Deployment Stage
  - stage: DeployToStaging
    dependsOn: Build
    jobs:
      - deployment: DeployStaging
        environment: 'Staging'
        strategy:
          runOnce:
            deploy:
              steps:
                # Step 1: Download build artifacts
                - task: DownloadBuildArtifacts@0
                  inputs:
                    buildType: 'current'
                    downloadType: 'single'
                    artifactName: 'python-package'
                    downloadPath: '$(System.DefaultWorkingDirectory)'

                # Step 2: Deploy to Azure Web App (Staging)
                - task: AzureWebApp@1
                  inputs:
                    azureSubscription: '$(azureSubscription)'
                    appType: 'webAppLinux'
                    appName: '$(appName)-staging'
                    package: '$(System.DefaultWorkingDirectory)/**/*.whl'

        # Optional: Adding a post-deployment approval step
        environment: 'Staging'
        approval:
          approvals:
            - type: manual
              name: "Approve Staging Deployment"
              timeout: "1h"
              reviewers:
                - group: "Staging Approvers"

  # Production Deployment Stage
  - stage: DeployToProduction
    dependsOn: DeployToStaging
    jobs:
      - deployment: DeployProduction
        environment: 'Production'
        strategy:
          runOnce:
            deploy:
              steps:
                # Step 1: Download build artifacts
                - task: DownloadBuildArtifacts@0
                  inputs:
                    buildType: 'current'
                    downloadType: 'single'
                    artifactName: 'python-package'
                    downloadPath: '$(System.DefaultWorkingDirectory)'

                # Step 2: Deploy to Azure Web App (Production)
                - task: AzureWebApp@1
                  inputs:
                    azureSubscription: '$(azureSubscription)'
                    appType: 'webAppLinux'
                    appName: '$(appName)-prod'
                    package: '$(System.DefaultWorkingDirectory)/**/*.whl'

        # Optional: Adding a post-deployment approval step
        environment: 'Production'
        approval:
          approvals:
            - type: manual
              name: "Approve Production Deployment"
              timeout: "1h"
              reviewers:
                - group: "Production Approvers"
```

### Explanation of Each Section

#### **Trigger**
- **Trigger:** The pipeline automatically runs whenever there is a change to the `main` branch, ensuring that the latest code is always built, tested, and deployed.

#### **Pool**
- **Pool:** The pipeline uses the latest Ubuntu-based virtual machine (`ubuntu-latest`) as the environment for executing the pipeline tasks.

#### **Variables**
- **Variables:** Variables are defined for reuse across the pipeline, such as 
    - Python version
    - application name
    - Azure subscription
- This makes the pipeline more flexible and easier to maintain.

#### **Build Stage**
- **Stage: Build:** This stage handles building the application.
- **UsePythonVersion:** Ensures the correct version of Python is used.
- **Install dependencies:** Installs necessary Python packages using `pip`.
- **Lint the code:** Linting checks the code for style issues and potential errors using `flake8` (optional but recommended).  
- **Run unit tests:** Executes unit tests using `pytest` to ensure the code works as expected.
- **==Package the application==:** Packages the Python application into distribution formats (e.g., source distribution and wheel).
- **==PublishBuildArtifacts==:** Publishes the built artifacts (e.g., the package files) for use in the deployment stages.

#### **Preprod(staging) Deployment Stage**
- **Stage: DeployToStaging:** This stage deploys the application to a staging environment for final testing and validation.
- **DownloadBuildArtifacts:** Downloads the artifacts generated in the build stage.
- **Deploy to Azure Web App:** Deploys the application to an Azure Web App instance designated for staging.
- **Approval Step (Optional):** After deployment to staging, manual approval is required before moving on to production. This allows for final validation in the staging environment.

#### **Production Deployment Stage**
- **Stage: DeployToProduction:** This stage deploys the application to the production environment.
- **DownloadBuildArtifacts:** Downloads the artifacts again to ensure the exact same package is deployed.
- **Deploy to Azure Web App:** Deploys the application to the production Azure Web App instance.
- **Approval Step (Optional):** Manual approval is required before the deployment to production, providing an additional safeguard.

### Production Considerations
1. **Approval Gates:** These are critical in production pipelines to prevent accidental or unauthorized deployments.
2. **Environment-Specific Configurations:** In a real-world scenario, the staging and production environments might have different configurations, such as database connections, API keys, etc. These should be managed securely using Azure Key Vault or environment-specific variables.
3. **Monitoring and Alerts:** After deploying to production, monitoring should be set up (e.g., Azure Monitor, Application Insights) to track the health and performance of the application.
4. **Rollback Strategies:** It's essential to have a rollback strategy in case something goes wrong in production. This can include automated rollback procedures or deployment slots in Azure Web Apps.