# CHANGELOG

## v1.6.0 — 2026-08-27
- 장기 연구용 OHLCV 기간과 Order Flow 기간을 분리.
- 기본 OHLCV 범위: 2019-07-10 ~ 2026-07-31.
- 기본 Order Flow 범위: 2021-05-18 ~ 2026-07-31.
- 최종 병합 CSV는 Order Flow 가능 구간만 생성.
- Bitget Futures Transaction History 공식 `size(base)` 헤더 지원.
- Transaction CSV 대용량 스트리밍 처리 추가.
- IndexedDB 기반 Order Flow 집계 저장/재개 기능 추가.
- 동일 파일 재가져오기 방지(파일명+크기+수정시간).
- Order Flow 기간의 전 OHLCV 봉 매칭이 완료되어야 병합 CSV 다운로드 허용.
- OHLCV 전체 CSV와 병합 CSV 다운로드를 분리.
- V1.5.1의 OHLCV 과거 페이지네이션 fallback 및 Candlestick CSV 보완 로직 유지.
