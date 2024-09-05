# Masking Vs Encryption Vs Tokenisation

In data engineering, **making, encryption, and tokenization** are techniques used to protect sensitive data and ensure its security during processing, storage, and transmission. Here's a brief overview of each:

### 1. **Masking:**
   - **Data Masking** is the process of obscuring or hiding sensitive data elements to protect them from unauthorized access. The original data is replaced with fake, but realistic data that looks similar to the original data but cannot be traced back to it.
   - **Use Case:** Masking is often used in testing environments where real data is not required, but developers need data that looks and behaves like the original.
   - **Example:** Replacing a credit card number `1234-5678-9012-3456` with `XXXX-XXXX-XXXX-3456`. 
   - Masking specific parts of the data, such as turning a Social Security Number 123-45-6789 into XXX-XX-6789 is called redaction
   - In the context of data masking, specific algorithms or methods aren't as standardized or universally recognized as AES in encryption.

### 2. **Encryption:**
   - **Data Encryption** is the process of converting data into a coded format using cryptographic algorithms, making it unreadable to anyone without the proper decryption key.
   - **Use Case:** Encryption is widely used to protect sensitive data at rest (stored data) and in transit (data being transmitted over networks).
   - **Example:** Encrypting a file so that its contents are unreadable without the correct decryption key, such as using AES (Advanced Encryption Standard) to encrypt a document.

### 3. **Tokenization:**
   - **Data Tokenization** is the process of replacing sensitive data with a unique identifier (token) that cannot be reversed or mapped back to the original data without a special tokenization system.
   - **Use Case:** Tokenization is commonly used in payment processing and protecting Personally Identifiable Information (PII). It is especially useful for reducing the risk of data breaches, as the tokenized data is not useful without the tokenization system.
   - **Example:** Replacing a credit card number `1234-5678-9012-3456` with a token like `TKN12345`, where the token has no meaningful relationship to the original data.
   - The tokenization approach it doesn’t rely on a standardized algorithm like AES in encryption. However, certain techniques and frameworks are commonly used to implement tokenization effectively like Hash-Based Tokenization. 
   - Hash-Based Tokenization: Sometimes, tokenization can use cryptographic hash functions (e.g., ==SHA-256==) to generate tokens. However, this is less common because hash functions are deterministic and don’t allow for easy detokenization.
   - Deterministic Tokenization: Consistent Token Generation: A specific piece of data always generates the same token. This approach allows for consistency across systems, so the same token is always returned for the same input.


### Summary:
- **Masking** is about obscuring data to prevent exposure.
- **Encryption** secures data by converting it into an unreadable format.
- **Tokenization** replaces sensitive data with non-sensitive placeholders that cannot be reversed without a specific system.

These techniques are crucial for ensuring data privacy and security, especially when handling sensitive or regulated information.