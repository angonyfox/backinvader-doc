You can run strategy using `bi run`

* pass parameter from command-line
* using configuration file

| Command Flag | Description |
|--------------|-------------|
| -c, --config CONFIG | using CONFIG file to run |
| -data name:kwargs, -d name:kwargs | using GenericCSVData to add data |
| -bundle name:kwargs | using data bundle to add data |
| -cerebro [kwargs] | pass cerebro options |
| --strategy module:name:kwargs | using strategy |
| --analyzer module:name:kwargs | using analyzer |
| --observer module:name:kwargs | using observer |
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
