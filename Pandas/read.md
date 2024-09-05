#### csv
```python
import pandas as pd

df = pd.read_csv('~/Downloads/tips.csv', skiprows = 5, delimiter = ',')
print(df)
```
#### methods in pandas
```python
import pandas as pd

methods = [i for i in dir(pd) if callable(getattr(pd, i)) and not i.startswith('_')]
print(', '.join(sorted(methods)))
```
ArrowDtype, BooleanDtype, Categorical, CategoricalDtype, CategoricalIndex, DataFrame, DateOffset, DatetimeIndex, DatetimeTZDtype, ExcelFile, ExcelWriter, Flags, Float32Dtype, Float64Dtype, Grouper, HDFStore, Index, Int16Dtype, Int32Dtype, Int64Dtype, Int8Dtype, Interval, IntervalDtype, IntervalIndex, MultiIndex, NamedAgg, Period, PeriodDtype, PeriodIndex, RangeIndex, Series, SparseDtype, StringDtype, Timedelta, TimedeltaIndex, Timestamp, UInt16Dtype, UInt32Dtype, UInt64Dtype, UInt8Dtype, array, bdate_range, concat, crosstab, cut, date_range, describe_option, eval, factorize, from_dummies, get_dummies, get_option, infer_freq, interval_range, isna, isnull, json_normalize, lreshape, melt, merge, merge_asof, merge_ordered, notna, notnull, option_context, period_range, pivot, pivot_table, qcut, read_clipboard, ==read_csv==, read_excel, read_feather, read_fwf, read_gbq, read_hdf, read_html, read_json, read_orc, read_parquet, read_pickle, read_sas, read_spss, read_sql, read_sql_query, read_sql_table, read_stata, read_table, read_xml, reset_option, set_eng_float_format, set_option, show_versions, test, timedelta_range, to_datetime, to_numeric, to_pickle, to_timedelta, unique, value_counts, wide_to_long
