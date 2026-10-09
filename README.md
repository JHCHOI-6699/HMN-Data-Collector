# HMN Data Collector v1.7.6 · OHLCV Diagnostic

Bitget Futures OHLCV 수집·검증용 GitHub Pages 버전입니다.

## v1.7.6 핵심 변경
- v1.7.5 기반
- 1m OHLC 오류 발생 시 V3 Historical Candles 수집값과 V2 Historical Candles 대체값을 동일 timestamp로 교차 비교
- 임의 OHLC 보정 없음
- 정상 대체값이 있으면 자동 복구
- 미복구 OHLC 오류는 `OHLC 오류 진단 CSV`로 내보내기
- 진단 CSV에 양쪽 O/H/L/C, 오류 유형, 값 동일 여부, 복구 여부 기록
- Bitget 웹 History data download에서 1m 파일이 제공되지 않는 경우 1D CSV를 1m에 병합하지 않도록 안내 강화

## 지원 시간봉
1m, 5m, 15m, 30m, 1H, 4H, 1D(Bitget UTC+8)

## 진단 순서
1. 문제 기간을 1m으로 수집·검증
2. OHLC 오류가 남으면 `OHLC 오류 진단 CSV 다운로드` 클릭
3. 생성된 CSV를 확인하거나 ChatGPT에 업로드
4. `primary_flags`, `alternate_flags`, `same_ohlc`로 원인 구분

가격을 강제로 수정하지 않습니다.
