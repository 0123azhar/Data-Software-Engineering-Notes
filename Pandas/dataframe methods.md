{{title}}

#### Passing dataframe to python [[builtin functions]]
```python
import pandas as pd

data = [['tom', 10], ['nick', 15], ['juli', 14], ['amal', 17], ['adam', 24]]
df = pd.DataFrame(data, columns=['name', 'age'])

print(len(df)) # 5
```


#### Commonly used dataframe methods and attributes
##### index
index can be duplicate, numeric, string (catagorical)
```python
import pandas as pd

data =  [['tom', 10, '1'], ['nick', 15, '2'], ['juli', 14, '4'], ['amal', 17, '3'], ['adam', 24, '5']]
df = pd.DataFrame(data, columns=['Name', 'Age', 'id'])
print(df)
#----------------#
print(df.index) # o/p: RangeIndex(start=0, stop=5, step=1)
df.index = [i for i in range(100,105,1)]
print(df.index) # Index([100, 101, 102, 103, 104], dtype='int64')
print(df)
```
##### set_index
```python
import pandas as pd

data =  [['tom', 10, '1', 'C'], ['nick', 15, '2', 'B'], ['juli', 14, '4', 'B'], ['amal', 17, '3', 'B'], ['adam', 24, '5', 'A']]
df = pd.DataFrame(data, columns=['Name', 'Age', 'id', 'grade'])
print(df)
#----------------#
print(df.index)
df.set_index('id', inplace = True)
print(df)
df.reset_index('id', inplace = True)
print(df)
```
##### sort_values
[[sorting]]
#### Attributes full list
1. T
2. at
3. attrs
4. axes
5. ==columns==
6. ==dtypes==
7. empty
8. flags
9. iat
10. [[#index]]
11. ndim
12. ==shape==
13. size
14. style
15. values
#### Methods full list
- abs, add, add_prefix, add_suffix, agg, aggregate, align, all, any, apply, applymap, asfreq, asof, assign, astype, at_time, 
- backfill, between_time, bfill, bool, boxplot, 
- clip, combine, combine_first, compare, convert_dtypes, copy, corr, corrwith, count, cov, cummax, cummin, cumprod, cumsum, 
- describe, diff, div, divide, dot, drop, drop_duplicates, droplevel, dropna, duplicated, 
- eq, equals, eval, ewm, expanding, explode, 
- ffill, fillna, filter, first, first_valid_index, floordiv, from_dict, from_records, 
- ge, get, groupby, gt, 
- head, hist, idxmax, 
- idxmin, iloc, infer_objects, info, insert, interpolate, isetitem, isin, isna, isnull, items, iterrows, itertuples, 
- join, keys, kurt, kurtosis, 
- last, last_valid_index, le, loc, lt, 
- map, mask, max, mean, median, melt, memory_usage, merge, min, mod, mode, mul, multiply, 
- ne, nlargest, notna, notnull, nsmallest, nunique, 
- pad, pct_change, pipe, pivot, pivot_table, plot, pop, pow, prod, product, 
- quantile, query, 
- radd, rank, rdiv, reindex, reindex_like, rename, rename_axis, reorder_levels, replace, resample, reset_index, rfloordiv, rmod, rmul, rolling, round, rpow, rsub, rtruediv, 
- sample, select_dtypes, sem, set_axis, set_flags, [[#set_index]], shift, skew, sort_index, [[#sort_values]], squeeze, stack, std, sub, subtract, sum, swapaxes, swaplevel, 
- tail, take, to_clipboard, to_csv, to_dict, to_excel, to_feather, to_gbq, to_hdf, to_html, to_json, to_latex, to_markdown, to_numpy, to_orc, to_parquet, to_period, to_pickle, to_records, to_sql, to_stata, to_string, to_timestamp, to_xarray, to_xml, transform, transpose, truediv, truncate, tz_convert, tz_localize, 
- unstack, update, 
- value_counts, var, 
- where, 
- xs
Code to generate dataframe attributes and methods above list
```python
import sys
import pandas as pd

print(pd.__version__)
print(sys.version)

df = pd.DataFrame() # empty dataframe

methods = [i for i in dir(df) if callable(getattr(df, i)) and not i.startswith('_')]
print(', '.join(sorted(methods)))

attributes = [i for i in dir(df) if not callable(getattr(df, i)) and not i.startswith('_')]
print('\n', ', '.join(sorted(attributes)))
```