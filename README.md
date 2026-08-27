# HMN Data Collector v1.5.1

Bitget USDT Futures OHLCV + Order Flow 수집기.

## v1.5.1 Hotfix
- OHLCV 역방향 페이지네이션 경계를 `oldest - 1ms`로 수정.
- v2 history-candles가 같은 과거 페이지를 반복하면 v3 history-candles를 fallback으로 시도.
- API가 요청 시작일까지 더 내려가지 못해도 이미 받은 데이터를 버리지 않고 `API floor`로 표시.
- Bitget 공식 **Futures Candlestick CSV** 복수 파일을 추가해 부족한 과거 OHLCV를 병합/중복제거/재검증 가능.
- Order Flow용 Futures Transaction History CSV 병합 기능 유지.
- 최종 CSV 다운로드는 요청기간 OHLCV가 완전하고, Order Flow 포함 옵션을 켰다면 Order Flow도 전 봉 매칭될 때만 허용.

## 사용 순서
1. 종목/시간봉/기간 선택.
2. `선택 시간봉 전체 수집·검증` 클릭.
3. API가 요청 시작일까지 도달하면 그대로 진행.
4. `API 시작점` 경고가 나오면 Bitget History data download의 Futures Candlestick 파일을 받아 `과거 OHLCV 보완`에 추가.
5. Order Flow 부족분이 있으면 Futures Transaction History CSV를 `과거 Order Flow 보완`에 추가.
6. 검증 완료 후 CSV 다운로드.

주의: 시간봉은 사용자가 선택한 Native timeframe 그대로 수집/집계합니다. 1H를 4H/1D로 합성하지 않습니다.
