# HMN Data Collector v1.7.1 — OHLCV Only

GitHub Pages에서 실행하는 Bitget Futures OHLCV 전용 수집기입니다.

## 기본 범위
- Symbol: `BTCUSDT`
- 기본 Timeframe: `1H`
- Start: `2019-07-10`
- End: `2026-07-31`
- 지원 Timeframe: `1H`, `4H`, `1D` (Bitget UTC+8 일봉)

## v1.7.1 핵심 변경
- `다운로드 가능한 전체기간 확인` 버튼을 복원했습니다.
- Bitget Historical Candles API를 실제로 과거 방향으로 탐색해 최초 제공 봉과 최신 마감 봉을 확인합니다.
- 확인된 최초 제공 봉보다 앞선 시간은 `API 제공 전 구간`으로 분리하고 누락으로 계산하지 않습니다.
- 예: 요청일이 2019-07-10이고 실제 최초 제공 봉이 2019-07-10 11:00 UTC라면 앞 11봉을 가짜 누락으로 만들지 않습니다.
- 실제 API 제공범위 안에서 예상/실제 봉 수가 일치하고 내부 누락 및 오류가 0이면 CSV 다운로드를 허용합니다.

## 기능
1. 다운로드 가능한 전체기간 확인 및 확인 범위 적용
2. Bitget Historical Candles API 전체기간 역방향 페이지네이션
3. 동일 과거 페이지 반복 시 V2/V3 fallback
4. 실제 API 최초 제공 시점 자동 확정
5. timestamp 중복 검사
6. 내부 누락 검사 및 누락봉 자동 재조회
7. OHLC 관계 검사
8. 숫자/음수 거래량 검사
9. API 제공범위 안에서 부족한 과거 구간은 Bitget Futures Candlestick CSV로 병합 보완
10. 모든 검증을 통과한 경우에만 CSV 다운로드 활성화

## 권장 사용 순서
1. 종목과 시간봉 선택
2. `다운로드 가능한 전체기간 확인` 클릭
3. 최초 제공 봉 / 마지막 확인 봉 확인
4. `확인된 전체기간 적용` 클릭
5. `OHLCV 전체 수집·검증` 클릭
6. `API 제공범위 기준 완전`, 내부 누락 0, 오류 0 확인
7. CSV 다운로드

## 출력 CSV
```text
timestamp,datetime_utc,open,high,low,close,volume_base,volume_quote
```

## 제거된 기능
v1.7.0부터 Order Flow / Transaction History / Buy-Sell / Delta / CVD 관련 기능은 전부 제거했습니다.

## 실행
정적 HTML이므로 `index.html`을 GitHub Pages 루트에 배포하면 됩니다.
