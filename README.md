# korexo_profile

Read KorEXO sonde profile CSV files.

Full package documentation is on [Read the Docs](https://korexo-profile.readthedocs.io/en/latest/).

## Install

```bash
$ pip install korexo_profile
```
## Usage

KorEXO file straight to a table:

```python
>>> import korexo_profile
>>> data = korexo_profile.read("../tests/example1_full.csv")
>>> df = korexo_profile.convert_datasets_to_df(data["datasets"])
```

Or, for the full set of information:

```python
>>> import korexo_profile
>>> data = korexo_profile.read("../tests/example2.csv")
>>> data.keys()
dict_keys(['metadata', 'datasets', 'dataframe'])
>>> df = data["dataframe"]
>>> df.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 9 entries, 0 to 8
Data columns (total 22 columns):
 #   Column               Non-Null Count  Dtype
---  ------               --------------  -----
 0   Date (MM/DD/YYYY)    9 non-null      object
 1   Time (HH:mm:ss)      9 non-null      object
 2   Time (Fract. Sec)    9 non-null      int64
 3   Site Name            9 non-null      object
 4   Cond µS/cm           9 non-null      int64
 5   Depth m              9 non-null      float64
 6   nLF Cond µS/cm       9 non-null      float64
 7   ODO % sat            9 non-null      float64
 8   ODO % local          9 non-null      float64
 9   ODO mg/L             9 non-null      float64
 10  ORP mV               9 non-null      float64
 11  Pressure psi a       9 non-null      float64
 12  Sal psu              9 non-null      int64
 13  SpCond µS/cm         9 non-null      float64
 14  TDS mg/L             9 non-null      int64
 15  pH                   9 non-null      float64
 16  pH mV                9 non-null      float64
 17  Temp °C              9 non-null      float64
 18  Vertical Position m  9 non-null      float64
 19  Battery V            9 non-null      float64
 20  Cable Pwr V          9 non-null      float64
 21  DTW                  1 non-null      float64
dtypes: float64(15), int64(4), object(3)
memory usage: 1.7+ KB
```

Or each dataset at a time:

```
>>> data["datasets"][0]
{'name': 'Date',
 'column': 'Date (MM/DD/YYYY)',
 'sensor': '',
 'mean': <NA>,
 'stdev': <NA>,
 'data': [datetime.date(2020, 10, 16),
  datetime.date(2020, 10, 16),
  datetime.date(2020, 10, 16),
  datetime.date(2020, 10, 16),
  datetime.date(2020, 10, 16),
  datetime.date(2020, 10, 16),
  datetime.date(2020, 10, 16),
  datetime.date(2020, 10, 16),
  datetime.date(2020, 10, 16)],
 'median': datetime.date(2020, 10, 16)}
>>> data["datasets"][1]
{'name': 'Time',
 'column': 'Time (HH:mm:ss)',
 'sensor': '',
 'mean': <NA>,
 'stdev': <NA>,
 'data': array(['15:49:33', '15:49:34', '15:49:35', '15:49:36', '15:49:37',
        '15:49:38', '15:49:39', '15:49:40', '15:49:41'], dtype=object),
 'median': '15:49:33'}
>>> data["datasets"][9]
{'name': 'ODO mg/L',
 'column': 'ODO mg/L',
 'sensor': '19D101830',
 'mean': 7.66,
 'stdev': 0.97,
 'data': array([9.5 , 9.5 , 9.49, 9.49, 9.5 , 9.49, 9.49, 9.5 , 9.49]),
 'median': 9.49}
```

And the metadata:

```python
>>> data["metadata"]
{'created_file': datetime.datetime(2022, 4, 7, 16, 45, 10, 874033),
 'modified_file': datetime.datetime(2022, 4, 7, 16, 45, 10, 875029),
 'created_info': '10/16/2020 6:21:53 AM,,,,,,,,,,,,,,,,,,,,',
 'header_line_no': 9,
 'params': ['Cond µS/cm',
  'Depth m',
  'nLF Cond µS/cm',
  'ODO % sat',
  'ODO % local',
  'ODO mg/L',
  'ORP mV',
  'Pressure psi a',
  'Sal psu',
  'SpCond µS/cm',
  'TDS mg/L',
  'pH',
  'pH mV',
  'Temp °C',
  'Vertical Position m',
  'Battery V',
  'Cable Pwr V',
  'DTW'],
 'sensors': ['19A103955',
  '19B104242',
  '19A103955',
  '19D101830',
  '19D101830',
  '19D101830',
  '19B105042',
  '19B104242',
  '19A103955',
  '19A103955',
  '19A103955',
  '19B105042',
  '19B105042',
  '19A103955',
  '19B104242',
  '19C000969',
  '19C000969',
  ''],
 'means': [1172.5,
  0.605,
  1277.2,
  85.5,
  85.6,
  7.66,
  47.1,
  0.859,
  0.64,
  1268.1,
  824,
  <NA>,
  -126,
  20.679,
  0.812,
  3.13,
  11.4,
  nan],
 'stdevs': [566.7,
  0.791,
  617.1,
  9.2,
  9.2,
  0.97,
  1.1,
  1.123,
  0.31,
  612.7,
  398,
  0.1,
  5.7,
  0.8,
  0.972,
  0,
  0,
  nan]}
```

Full package documentation is on [Read the Docs](https://korexo-profile.readthedocs.io/en/latest/).
