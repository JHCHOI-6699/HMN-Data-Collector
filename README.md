# HMN Data Collector v1.7.7 · OHLCV Gap-Open Validation

Bitget Futures OHLCV 수집·검증용 GitHub Pages 버전입니다.

## v1.7.7 핵심 변경
- v1.7.6 진단 CSV 분석 결과를 반영했습니다.
- 진단 파일의 오류 2,472봉은 전부 `LOW_GT_OPEN` 유형이었습니다.
- V2/V3 양쪽 값이 확보된 2,072봉은 OHLC가 완전히 동일했고 정상 대체값은 0봉이었습니다.
- Bitget 구형 1m 데이터에서 `open == 직전 봉 close`이면서 open만 현재 봉 high/low 범위 밖에 있는 경우를 `Bitget gap-open`으로 분리합니다.
- gap-open은 원본 가격을 수정하지 않고 검증 허용하며 별도 개수로 표시합니다.
- `high >= low`, `close ∈ [low, high]`, 양수/숫자 조건은 계속 엄격하게 검사합니다.
- open이 범위 밖인데 직전 close와 일치하지 않는 경우는 기존처럼 실제 OHLC 오류로 처리하고 V2/V3 교차검증을 수행합니다.
- 임의 OHLC 보정 없음.

## 지원 시간봉
1m, 5m, 15m, 30m, 1H, 4H, 1D(Bitget UTC+8)

## 권장 검증 순서
1. 문제 기간을 다시 수집·검증합니다.
2. 검증 결과의 `Bitget gap-open 허용` 수와 `OHLC 오류` 수를 확인합니다.
3. `OHLC 오류 0`, 내부 누락 0, 중복 0이면 CSV 다운로드가 활성화됩니다.
4. `OHLC 오류`가 남을 때만 진단 CSV를 내려받습니다.

가격을 강제로 수정하지 않습니다.
