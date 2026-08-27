# HMN Data Collector

**현재 버전:** 1.5.0  
**기준:** Bitget USDT Futures / 선택 시간봉 Native 수집 + 동일 시간봉 Order Flow 병합

## 핵심 변경

V1.4의 `1H Master -> 4H/1D 파생`을 기본 경로에서 제거했습니다.

사용자는 시간봉을 선택합니다.

- 1H 선택 -> Bitget native 1H OHLCV 수집 + 1H Order Flow 병합
- 4H 선택 -> Bitget native 4H OHLCV 수집 + 4H Order Flow 병합
- 1D 선택 -> Bitget native 1D OHLCV 수집 + 1D Order Flow 병합

즉 1H 4개를 합쳐 4H를 만들거나, 1H 24개를 합쳐 1D를 만드는 것을 기본 데이터 경로로 사용하지 않습니다.

## 사용법

1. 종목 선택
2. 시간봉 선택
3. 시작일/종료일 선택
4. `선택 시간봉의 Order Flow를 CSV에 포함`은 기본 ON
5. `선택 시간봉 전체 수집·검증`
6. Order Flow까지 요청기간 전체가 매칭되면 한 번에 병합 CSV 다운로드

CSV:

```text
timestamp,datetime_utc,open,high,low,close,volume_base,volume_quote,
taker_buy_base,taker_sell_base,delta_base,buy_ratio,sell_ratio,total_active_base,cvd
```

## 매우 중요한 데이터 소스 차이

OHLCV historical candles는 기존 V1.2와 동일하게 페이지네이션하여 시작일~종료일 전체를 자동 수집할 수 있습니다.

하지만 Bitget Active Buy/Sell 공개 엔드포인트는 historical `start/end` 페이지네이션이 없습니다. 따라서 공개 Active Buy/Sell 응답 범위보다 오래된 Order Flow를 요청하면 OHLCV는 완성되어도 Order Flow가 부족할 수 있습니다.

V1.5는 이 경우 빈 값을 섞어서 다운로드하지 않습니다. `Order Flow N봉 부족`으로 다운로드를 차단합니다.

과거 전체 Order Flow가 필요하면 Bitget 공식 Futures Transaction History CSV를 가져오면 됩니다. V1.5는 그 체결을 **현재 선택한 시간봉으로 직접 집계**하여 현재 OHLCV에 병합합니다. 1H 중간 집계는 사용하지 않습니다.

## Direct Active Buy/Sell 자동조회

HMN V1.5에서 직접 병합 대상으로 둔 시간봉:

```text
1H -> period=1h
4H -> period=4h
1D(Bitget) -> period=1d
```

`1Dutc`는 거래소 native 일봉과 경계가 다르므로 Direct 1D Order Flow를 자동 병합하지 않습니다. Transaction History를 UTC 경계로 직접 집계하면 사용할 수 있습니다.

기타 시간봉은 OHLCV 직접수집 기능은 유지합니다. Order Flow는 Transaction History CSV를 선택한 시간봉으로 직접 집계할 수 있습니다.

## 검증 원칙

- 미확정 봉 제외
- OHLCV 중복/누락/시간불연속/OHLC 오류 검사
- 누락 봉 개별 API 복구
- Order Flow 포함 다운로드는 OHLCV 각 timestamp에 Order Flow가 모두 존재할 때만 허용
- 봉 색으로 매수/매도를 추정하지 않음
- Transaction History의 buy/sell을 taker 방향으로 집계
- CVD는 최종 선택기간의 선택 시간봉 delta를 시간순 누적

## V1.4와의 관계

V1.4의 1H Master/상위시간봉 파생은 연구용 아이디어로 보존할 수 있지만, V1.5의 공식 다운로드 경로는 **선택한 native 시간봉 직접 수집**입니다.
