# Changelog

## v1.7.7
- Added legacy Bitget 1m gap-open validation policy based on v1.7.6 diagnostic results.
- Accepts open outside [low, high] only when open equals the immediately previous candle close and close/high/low are internally valid.
- Preserves raw Bitget OHLC values; no synthetic price correction.
- Reports accepted gap-open candles separately.
- Keeps strict V2/V3 cross-validation for all remaining OHLC violations.

## v1.7.6
- Added OHLC diagnostic export.
- Cross-compares 1m V3 history-candles with V2 history-candles by exact timestamp.
- Records OHLC violation type and whether both endpoints return identical values.
- Keeps automatic replacement only when alternate source is OHLC-valid.
- Removed misleading suggestion to use 1D web-download data as a 1m repair source.
