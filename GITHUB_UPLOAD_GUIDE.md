# GitHub 업로드 가이드 — v1.7.3

기존 `HMN-Data-Collector` 저장소를 삭제할 필요가 없습니다.

1. 이 ZIP을 압축 해제합니다.
2. GitHub 저장소 → **Code → Add file → Upload files** 로 이동합니다.
3. 아래 4개 파일을 모두 업로드해 기존 파일에 덮어씁니다.
   - `index.html`
   - `README.md`
   - `CHANGELOG.md`
   - `GITHUB_UPLOAD_GUIDE.md`
4. Commit message 예: `Update HMN Data Collector to v1.7.3`
5. **Commit changes**를 누릅니다.
6. 기존 GitHub Pages 설정 `main / (root)`은 변경하지 않습니다.
7. Actions에서 `pages build and deployment`가 초록 체크인지 확인합니다.
8. 기존 Pages 주소를 열고 **Ctrl + F5**를 누릅니다.
9. 화면 상단에 `v1.7.3 · OHLCV Only`가 표시되는지 확인합니다.

## 사용 순서

1. 종목과 시간봉(5m/15m/30m/1H/4H/1D)을 선택합니다.
2. **다운로드 가능한 전체기간 확인**을 누릅니다.
3. **확인된 전체기간 적용**을 누릅니다.
4. **OHLCV 전체 수집·검증**을 실행합니다.
5. 내부 누락과 오류가 0이고 기간 완전성이 통과하면 CSV를 다운로드합니다.

5m 전기간은 데이터가 매우 많아 수분 이상 걸릴 수 있습니다.
