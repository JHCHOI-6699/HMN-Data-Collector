# HMN Data Collector v1.7.4 · OHLCV Only

Bitget USDT Futures native OHLCV 수집/검증 도구입니다.

지원 시간봉: 1m, 5m, 15m, 30m, 1H, 4H, Bitget 1D.

## v1.7.4 핵심
- 1m은 Bitget V3 Historical Candles를 우선 사용합니다.
- OHLC 관계가 깨진 봉은 V2/V3를 다시 조회하여 원본 데이터가 정상인 경우에만 교체합니다.
- 가격을 임의로 수정하거나 high/low를 강제로 재계산하지 않습니다.
- 중복/내부누락/OHLC/숫자/음수거래량 오류가 모두 0일 때만 CSV 다운로드가 활성화됩니다.
- `다운로드 가능한 전체기간 확인` 기능을 유지합니다.

장기간 1m은 브라우저 메모리와 API 호출량이 매우 크므로 월별/분기별 수집을 권장합니다.
