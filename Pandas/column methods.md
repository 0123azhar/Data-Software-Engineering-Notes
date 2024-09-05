202408240331
# column methods

#### commonly used methods
##### value_counts
```python
import pandas as pd

data =  [['tom', 10, '1', 'C'], ['nick', 15, '2', 'B'], ['juli', 14, '4', 'B'], ['amal', 17, '3', 'B'], ['adam', 24, '5', 'A'], ['adam', 18, '3', 'F']]
df = pd.DataFrame(data, columns=['name', 'age', 'id', 'grade'])
print(df)
#----------------#

print(df.grade.value_counts())
```
##### fillna
```python
import pandas as pd

data =  [['tom', 10, '1', 'C'], ['nick', 15, '2', 'B'], ['juli', None, '4', 'B'], ['amal', 17, '3', 'B'], ['adam', 24, '5', 'A'], ['adam', 18, '3', 'F']]
df = pd.DataFrame(data, columns=['name', 'age', 'id', 'grade'])
print(df)
#----------------#
df.age.fillna(df.age.mean(), inplace = True)
print(df)
```
##### apply
```python
import pandas as pd

data =  [['tom', 10, '1', 'C'], ['nick', 15, '2', 'B'], ['juli', None, '4', 'B'], ['amal', 17, '3', 'B'], ['adam', 24, '5', 'A'], ['adam', 18, '3', 'F']]
df = pd.DataFrame(data, columns=['name', 'age', 'id', 'grade'])
print(df)
#----------------#

df['double_age'] = df.age.apply(lambda x: x*2)
print(df)
```

#### All dataframe columns attributes and methods
```python
import pandas as pd

data = [['tom', 10], ['nick', 15], ['juli', 14], ['amal', 17], ['adam', 24]]
df = pd.DataFrame(data, columns=['name', 'age'])

print(sorted([i for i in dir(df.name) if  not i.startswith('_')]))
```
T, abs, add, add_prefix, add_suffix, agg, aggregate, align, all, any, [[#apply]], argmax, argmin, argsort, array, asfreq, asof, astype, at, at_time, attrs, autocorr, axes, 
backfill, between, between_time, bfill, bool, 
case_when, clip, combine, combine_first, compare, convert_dtypes, copy, corr, count, cov, cummax, cummin, cumprod, cumsum, 
describe, diff, div, divide, divmod, dot, drop, drop_duplicates, droplevel, dropna, dtype, dtypes, duplicated, 
empty, eq, equals, ewm, expanding, explode, 
factorize, ffill, [[#fillna]], filter, first, first_valid_index, flags, floordiv, 
ge, get, groupby, gt, 
hasnans, head, hist, 
iat, idxmax, idxmin, iloc, index, infer_objects, info, interpolate, is_monotonic_decreasing, is_monotonic_increasing, is_unique, isin, isna, isnull, item, items, 
keys, kurt, kurtosis, 
last, last_valid_index, le, list, loc, lt, 
map, mask, max, mean, median, memory_usage, min, mod, mode, mul, multiply, 
name, nbytes, ndim, ne, nlargest, notna, notnull, nsmallest, nunique, 
pad, pct_change, pipe, plot, pop, pow, prod, product, 
quantile, 
radd, rank, ravel, rdiv, rdivmod, reindex, reindex_like, rename, rename_axis, reorder_levels, repeat, replace, resample, reset_index, rfloordiv, rmod, rmul, rolling, round, rpow, rsub, rtruediv, 
sample, searchsorted, sem, set_axis, set_flags, shape, shift, size, skew, sort_index, sort_values, squeeze, std, str, struct, sub, subtract, sum, swapaxes, swaplevel, 
tail, take, to_clipboard, to_csv, to_dict, to_excel, to_frame, to_hdf, to_json, to_latex, to_list, to_markdown, to_numpy, to_period, to_pickle, to_sql, to_string, to_timestamp, to_xarray, transform, transpose, truediv, truncate, tz_convert, tz_localize, 
unique, unstack, update, 
[[#value_counts]], values, var, view, 
where, 
xs