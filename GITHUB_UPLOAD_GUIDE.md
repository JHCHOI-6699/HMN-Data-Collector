# GitHub Pages 교체 방법 — v1.7.1

기존 `HMN-Data-Collector` 저장소를 삭제하지 마세요.

1. 이 ZIP을 압축 해제합니다.
2. GitHub 저장소 → `Code` → `Add file` → `Upload files`.
3. 다음 4개 파일을 업로드합니다.
   - `index.html`
   - `README.md`
   - `CHANGELOG.md`
   - `GITHUB_UPLOAD_GUIDE.md`
4. 기존 같은 이름 파일은 삭제하지 않고 그대로 덮어씁니다.
5. Commit message 예: `Update HMN Data Collector to v1.7.1`
6. `Commit changes`를 누릅니다.
7. 기존 GitHub Pages 설정 `main / (root)`은 변경하지 않습니다.
8. Actions에서 `pages build and deployment`가 초록 체크인지 확인합니다.
9. 기존 Pages 주소를 열고 `Ctrl + F5`로 강력 새로고침합니다.
10. 화면 상단에 `v1.7.1 · OHLCV Only`가 보이면 교체 완료입니다.

## 권장 사용 순서
1. 종목/시간봉 선택
2. `다운로드 가능한 전체기간 확인` 클릭
3. `최초 제공 봉`과 `마지막 확인 봉` 확인
4. `확인된 전체기간 적용` 클릭
5. `OHLCV 전체 수집·검증` 클릭
6. 검증 결과에서 `기간 완전성: API 제공범위 기준 완전` 또는 `완전` 확인
7. 내부 누락/중복/OHLC/숫자/음수 거래량 오류가 모두 0인지 확인
8. `검증 완료 OHLCV CSV 다운로드` 클릭

`API 제공 전 구간`은 실제 Bitget 데이터가 존재하지 않는 앞 경계이므로 가짜 캔들로 채우지 않습니다.
