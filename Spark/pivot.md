```python
get one row for each date and getting the province names as columns. 

pivotedTimeprovince = timeprovince.groupBy('date').pivot('province')

.agg(F.sum('confirmed').alias('confirmed') , F.sum('released').alias('released'))
```

![[Pasted image 20240818104704.png]]