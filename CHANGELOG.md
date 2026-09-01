# Changelog

## v1.7.1 — 2026-09-01
- `다운로드 가능한 전체기간 확인` 기능 복원
- 최초 제공 봉과 최신 마감 봉을 API에서 직접 탐색
- 확인된 최초 제공 봉보다 앞선 요청시간을 `API 제공 전 구간`으로 분리
- API 제공 전 구간을 누락으로 잘못 계산하던 경계 검증 수정
- 최초 제공 봉부터 종료일까지 완전하면 `API 제공범위 기준 완전`으로 PASS
- `확인된 전체기간 적용` 버튼 추가
- 최초 제공 시점 / API 제공 전 봉 수를 검증 결과에 표시
- 기존 장기 페이지네이션, V2/V3 fallback, 누락 자동복구, Candlestick CSV 보완 유지
- Order Flow 기능은 계속 미포함

## v1.7.0 — 2026-09-01
- OHLCV 전용 버전으로 단순화
- Order Flow 다운로드/체결 CSV/IndexedDB/병합 기능 전체 제거
- 기본 OHLCV 범위 유지: 2019-07-10 ~ 2026-07-31
- 1H / 4H / Bitget 1D OHLCV 지원 유지
- 장기 Historical Candles 페이지네이션 유지
- V2/V3 과거 페이지 fallback 유지
- 내부 누락봉 자동 복구 유지
- Bitget Futures Candlestick CSV 보완 유지
- OHLCV 전체기간 검증 통과 시에만 CSV 다운로드 허용
