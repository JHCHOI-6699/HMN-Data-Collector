# Changelog

## v1.7.6
- Added OHLC diagnostic export.
- Cross-compares 1m V3 history-candles with V2 history-candles by exact timestamp.
- Records OHLC violation type and whether both endpoints return identical values.
- Keeps automatic replacement only when alternate source is OHLC-valid.
- Removed misleading suggestion to use 1D web-download data as a 1m repair source.
