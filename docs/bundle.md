Data bundle is data source to use in strategy. Data bundle can be:

* Local file
* Data source that use API to fetch data

## Add new data bundle
To install data bundle, run `bi register` command.
```
bi register [--format FORMAT] [--parameter kwargs] name
```
| Command Flag | Description |
|--------------|-------------|
| NAME | bundle name |
| -f, --format FORMAT | Data Format or Data Feed Class |
| -p, --parameter kwargs | Parameter for Data bundle |

- FORMAT:   
    Available Data Format from backtrader
    - btcsv
    - generic
    - influxdb
    - mt4csv
    - quandl
    - sierracsv
    - vchartcsv
    - vcfile
    - yahoo
    - yahoocsv
    - yahoocsv_unreversed
  
    Data Feed Class can be specified with the following form:  

    - module.classname
    - module.submodule.classname

- Parameter: each data format need parameters. Some backtrader data feed class must pass `dataname` parameter to provide location of file. The argument can be specified with `key=value`. For multiple parameters use `-p key1=val1 -p key2=val2`

#### Example
```
$>bi register -f yahoocsv -p dataname="backinvader-example/data/orcl-1995-2014.txt" orcl19952014
```
## Listing Data bundles

To see a list of data bundles that are available after registered, run `bi bundles`

```
$>bi bundles

SP500-2010-2020
EURUSD-1980-2015
```

## Data bundle information
Use `bi bundle` to show information about data bundle.
```
$>bi bundle NAME
```
## Remove data bundle
Use `bi unregister` command to remove specified data bundle
```
$>bi unregister NAME
```
