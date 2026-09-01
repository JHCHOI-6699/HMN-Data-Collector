# HMN Data Collector v1.7.0 — OHLCV Only

GitHub Pages에서 실행하는 Bitget Futures OHLCV 전용 수집기입니다.

## 기본 범위
- Symbol: `BTCUSDT`
- 기본 Timeframe: `1H`
- Start: `2019-07-10`
- End: `2026-07-31`
- 지원 Timeframe: `1H`, `4H`, `1D` (Bitget UTC+8 일봉)

## 기능
1. Bitget Historical Candles API 전체기간 역방향 페이지네이션
2. 동일 과거 페이지 반복 시 V2/V3 fallback
3. timestamp 중복 검사
4. 내부 누락 검사 및 누락봉 자동 재조회
5. OHLC 관계 검사
6. 숫자/음수 거래량 검사
7. API로 부족한 과거 구간은 Bitget Futures Candlestick CSV로 병합 보완
8. 요청기간 완전성 및 모든 검증을 통과한 경우에만 CSV 다운로드 활성화

## 출력 CSV
```text
timestamp,datetime_utc,open,high,low,close,volume_base,volume_quote
```

## 제거된 기능
v1.7.0부터 Order Flow / Transaction History / Buy-Sell / Delta / CVD 관련 기능은 전부 제거했습니다.

## 실행
정적 HTML이므로 `index.html`을 GitHub Pages 루트에 배포하면 됩니다.
