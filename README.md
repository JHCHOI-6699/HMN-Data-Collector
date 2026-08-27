# HMN Data Collector v1.6.0

장기 HMN 연구용 Bitget USDT Futures OHLCV + Order Flow 병합 수집기입니다.

## 기본 연구 범위
- OHLCV: **2019-07-10 ~ 2026-07-31**
- Order Flow: **2021-05-18 ~ 2026-07-31**
- 기본 시간봉: **1H**
- 지원 시간봉: 1H / 4H / Bitget 1D(UTC+8 경계)

날짜는 화면에서 변경할 수 있습니다.

## 데이터 소스
### OHLCV
1. Bitget Historical Candles API로 전체기간 수집
2. API가 요청 시작일까지 내려가지 못하면 Bitget History data download의 `Futures → Candlestick` CSV로 보완

### Order Flow
Bitget History data download의 `Futures → Transaction history → Daily` CSV를 사용합니다.

공식 헤더 예시:
- `timestamp`
- `trade_id`
- `price`
- `side`
- `volume(quote)`
- `size(base)`

v1.6.0은 `size(base)`를 직접 인식합니다.

## 처리 방식
- Transaction History의 개별 체결을 선택한 시간봉으로 직접 집계합니다.
- 1H를 중간 Master로 만들어 4H/1D를 파생하지 않습니다.
- Buy 체결 합계 → `taker_buy_base`
- Sell 체결 합계 → `taker_sell_base`
- `delta_base = taker_buy_base - taker_sell_base`
- `buy_ratio`, `sell_ratio`, `total_active_base`, `cvd` 계산
- 최종 병합은 OHLCV timestamp 기준

## 대용량 과거 체결 처리
- CSV 파일을 한 파일씩 스트리밍 처리하므로 `file.text()`로 전체 파일을 한꺼번에 메모리에 올리지 않습니다.
- 집계된 시간봉 Order Flow만 IndexedDB에 저장합니다.
- 여러 번에 나눠 CSV를 가져와도 이전 집계 결과가 유지됩니다.
- 동일 파일(파일명+크기+수정시간)은 중복 가져오기를 건너뜁니다.
- 서로 다른 CSV 파일의 날짜 구간이 겹치면 체결이 중복 합산될 수 있으므로 겹치지 않는 파일을 사용하세요.

## 최종 검증 조건
`OHLCV + Order Flow 병합 CSV 다운로드`는 다음을 모두 만족해야 활성화됩니다.
1. OHLCV 전체 요청기간 완전성 통과
2. OHLC 오류 0
3. 내부 누락 0
4. 중복 0
5. Order Flow 기간의 모든 OHLCV 봉에 Order Flow 버킷 존재

## 다운로드 결과
### OHLCV 전체 CSV
2019년 시작 구간부터 OHLCV 종료일까지의 순수 OHLCV.

### OHLCV + Order Flow 병합 CSV
Order Flow 시작일부터 종료일까지의 겹치는 구간만 생성합니다.

열:
`timestamp, datetime_utc, open, high, low, close, volume_base, volume_quote, taker_buy_base, taker_sell_base, delta_base, buy_ratio, sell_ratio, total_active_base, cvd`

## GitHub Pages
저장소 루트에 `index.html`과 이 파일들을 업로드한 뒤:
- Settings → Pages
- Deploy from a branch
- `main`
- `/(root)`

기존 Pages 저장소를 업데이트하는 경우 파일을 덮어쓰고 Commit하면 자동 재배포됩니다.
