# Changelog

## v1.7.4
- 1m 장기 OHLCV의 기본 수집 소스를 Bitget V3 `market/history-candles` 우선으로 변경.
- 1m 페이지 크기를 V3 최대치(100)에 맞춤.
- OHLC 관계 오류가 발견된 봉은 V2/V3 대체 endpoint로 재조회하여 유효한 원본 봉으로만 교체.
- high/low 값을 임의로 보정하는 방식은 사용하지 않음.
- 검증 결과에 `OHLC 교차복구` 건수 추가.
- 1m/5m/15m/30m/1H/4H/1D 지원 유지.

## v1.7.3
- 1m native OHLCV 수집 추가.
