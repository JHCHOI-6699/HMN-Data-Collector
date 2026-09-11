# Changelog

## v1.7.5
- Fixed very slow / apparently stalled OHLC anomaly cross-validation.
- Replaced per-candle V2/V3 exact re-query loop with page-wise bulk cross-validation.
- Added continuous cross-validation progress status.
- Added bounded page scan so cross-validation terminates instead of generating thousands of exact-candle calls.
- Preserved strict rule: only replace a candle when an alternate Bitget endpoint returns the same timestamp with valid OHLC.
- Improved final validation message to state whether failure is due to period coverage, missing bars, OHLC errors, numeric errors, or negative volume.

## v1.7.4
- 1m V3-first historical candles.
- OHLC cross-check/recovery added.
