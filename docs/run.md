You can run strategy using `bi run`

* pass parameter from command-line
* using configuration file

| Command Flag | Description |
|--------------|-------------|
| -c, --config CONFIG | using CONFIG file to run |
| --data name:kwargs, -d name:kwargs | using GenericCSVData to add data |
| --bundle name:kwargs | using data bundle to add data |
| --cerebro kwargs, -ce kwargs | pass cerebro options |
| --strategy module:name:kwargs, -st module:name:kwargs | using strategy |
| --analyzer module:name:kwargs, -an module:name:kwargs | using analyzer |
| --observer module:name:kwargs, -ob module:name:kwargs | using observer |
| --nostdstats | Disable the standard statistics observers |
| --cash CASH | Cash to set to the broker |
| --commission COMMISSION | COMMISSION value to set |
| --margin MARGIN | MARGIN value to set |
| --mult MULT | Multiplier to use |
| --interest INTEREST | Credit Interest rate to apply (0.0x) |
| --interest_long | Apply credit interest to long positions |
| --slip_perc SLIP_PERC | Enable slippage with percentage value |
| --slip_fixed SLIP_FIXED | Enable slippage with a fixed point value |
| --slip_open | enable slippage for when matching opening prices |
| --no-slip_match | Disable slip_match, ie: matching capped at high-low if slippage goes over those limits |
| --slip_out | with slip_match enabled, match outside high-low |
| --plot [kwargs] | apply parameter for plotting |


## Pass Parameter from command-line

### Adding data source

#### Using --data
Data to be added to the system using GenericCSVData. This option can be specified multiple times.

The argument can be specified with the following form `filename:kwargs`

`kwargs` is optional.The available kwargs to bundle are:

- fromdate
- todate
- timeframe
- compression
- resample
- replay
- filter

*Example*
```
-d /path/to/filename.csv:a=1,b=2
```

#### Using --bundle
Data Bundle to be added to the system. This option can be specified multiple times.

The argument can be specified with the following form `bundlename:kwargs`

`kwargs` is optional.The available kwargs to bundle are:

- fromdate
- todate
- timeframe
- compression
- resample
- replay
- filter

timeframe, resample and replay argument can be specified as 
[ticks, microseconds, seconds, minutes, days, weeks, months, years]
and [T, MS, S, M, D, W, MN, Y] with integer.
For example, M5 is 5 mins

**Example**
```
-b mybundle:a=1,b=2
```

### Cerebro options
The passed kwargs will be passed directoly to the cerebro instance created for the execution

The available kwargs to cerebro are:

- preload (default: True)
- runonce (default: True)
- maxcpus (default: None)
- stdstats (default: True)
- live (default: False)
- exactbars (default: False)
- writer (default False)
- oldbuysell (default False)
- tradehistory (default False)

**Example**
```
-ce preload=False

For multiple kwargs:

-ce preload=False -ce maxcpu=1
```

### Adding Strategy
Using `--strategy` or `-st` to run strategy. This option can be specified multiple times.

The argument can be specified with the following form `module.classname:kwargs`

kwargs is optional

If module is omitted then class name will be sought in
the built-in strategies module. Such as in `classname:kwargs` or `classname` 

module can specified as path to file (must ending with .py)
that contain class definition `filepath:classname` or `filepath:classname:kwargs`

**Example**
```
-st mymod.myclass:a=1,b=2
-st /strategy/mystrategyfile:MyStrategyClass:a=1,b=2
```

### Adding Analyzer
Using `--analyzer` or `-an` to add analyzer. This option can be specified multiple times.

The argument can be specified with the following form `module.classname:kwargs`

kwargs is optional

If module is omitted then class name will be sought in
the built-in analyzers module. Such as in `classname:kwargs` or `classname` 

module can specified as path to file (must ending with .py)
that contain class definition `filepath:classname` or `filepath:classname:kwargs`

**Example**
```
-an SQN
-an mymod.myclass:a=1,b=2
-an /analyzer/myanalyzerfile:MyAnalyzerClass:a=1,b=2
```

### Adding Observer
Using `--observer` or `-ob` to add observer. This option can be specified multiple times.

The argument can be specified with the following form `module.classname:kwargs`

kwargs is optional

If module is omitted then class name will be sought in
the built-in observers module. Such as in `classname:kwargs` or `classname` 

module can specified as path to file (must ending with .py)
that contain class definition `filepath:classname` or `filepath:classname:kwargs`

**Example**
```
-ob DrawDown
-ob mymod.myclass:a=1,b=2
-ob /observer/myobserverfile:MyObserverClass:a=1,b=2
```

### Plotting
Apply parameter for plotting

- style: [bar, line] to plot candlesticks/line
- plot_mode: [single, tabs] to generate single/tabs page
- output_dir: directory to write report
- filename: report name

**Example**
```
--plot style="bar"
-p style="bar" -p filename="result"
```

