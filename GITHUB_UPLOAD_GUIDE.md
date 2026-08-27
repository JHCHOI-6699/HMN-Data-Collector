# GitHub 교체 업로드 가이드 — v1.6.0

1. 기존 `HMN-Data-Collector` GitHub 저장소의 **Code** 화면을 엽니다.
2. **Add file → Upload files**를 누릅니다.
3. 이 폴더의 다음 파일을 업로드합니다.
   - `index.html`
   - `README.md`
   - `CHANGELOG.md`
   - `GITHUB_UPLOAD_GUIDE.md`
4. 기존 같은 이름 파일은 삭제하지 말고 그대로 덮어씁니다.
5. Commit message 예: `Update HMN Data Collector to v1.6.0`
6. **Commit changes**를 누릅니다.
7. 기존 GitHub Pages 설정(`main`, `/(root)`)은 변경하지 않습니다.
8. Actions에서 `pages build and deployment`가 초록색 체크인지 확인합니다.
9. 기존 Pages 주소를 열고 `Ctrl + F5`를 누릅니다.
10. 화면 상단에 `HMN Data Collector v1.6.0`이 보이는지 확인합니다.

## 처음 사용할 때
1. BTCUSDT / 1H 확인
2. OHLCV 2019-07-10 ~ 2026-07-31 확인
3. Order Flow 2021-05-18 ~ 2026-07-31 확인
4. `OHLCV 전체 수집·검증`
5. OHLCV가 부족하면 Candlestick CSV로 보완
6. Bitget Transaction History Daily CSV를 여러 번 나눠 가져오기
7. Order Flow 매칭이 전체 완료될 때까지 반복
8. `OHLCV + Order Flow 병합 CSV 다운로드`

## 주의
Bitget Transaction History 파일이 ZIP으로 내려오면 브라우저에 넣기 전에 압축을 풀고 CSV 파일을 선택하세요.
