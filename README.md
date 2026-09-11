# HMN Data Collector v1.7.3 · OHLCV Only

Bitget USDT Futures의 OHLCV를 장기간 수집·검증하고 CSV로 다운로드하는 GitHub Pages용 단일 페이지 도구입니다.

## 지원 시간봉

- 1m
- 5m
- 15m
- 30m
- 1H
- 4H
- 1D (Bitget UTC+8 일봉 경계)

## 핵심 기능

- `다운로드 가능한 전체기간 확인`
- 확인된 Bitget 최초 제공 봉을 유효 시작점으로 사용
- Historical Candles API 과거 방향 페이지네이션
- v2 반복/바닥 감지 시 v3 history-candles fallback
- 누락 봉 자동 재조회 및 복구
- 중복, 내부 누락, OHLC, 숫자, 음수 거래량 검증
- API 제공범위보다 앞선 요청 시간은 가짜 누락으로 계산하지 않음
- 필요시 Bitget Futures Candlestick CSV 병합·재검증
- 검증 통과 후에만 CSV 다운로드 활성화

## CSV 열

`timestamp,datetime_utc,open,high,low,close,volume_base,volume_quote`

## 1m 장기 수집 주의

2019년부터 1m 데이터를 한 번에 수집하면 수백만 개의 봉이 될 수 있습니다. 브라우저 메모리 사용량과 처리시간이 매우 커질 수 있으므로 **1m은 기간을 나눠 수집하는 것을 권장**합니다. PC 데스크톱 브라우저를 사용하고, 작업 중에는 탭을 닫거나 새로고침하지 마세요.

5m도 장기간 전체 수집 시 수십만 개의 봉이 될 수 있으므로 같은 주의가 필요합니다.

## GitHub Pages

저장소 루트에 `index.html`을 두고 Pages를 `main / (root)`에서 배포하면 됩니다.
