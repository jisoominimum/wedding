# 모바일 청첩장

## 1. 내용 수정
`index.html` 파일을 열어서 아래를 본인 정보로 바꾸세요.
- 신랑·신부 이름, 부모님 성함
- 예식 일시 / 장소 / 주소
- 계좌번호 (은행 + 번호)
- 연락처 (`tel:`, `sms:` 뒤의 번호)
- `<meta property="og:...">` 의 제목/설명 (카톡 공유 미리보기)

## 2. 사진 구조
- **표지**: `images/main.jpg`
- **갤러리**: `images/web/` 폴더 안의 사진들 (원본은 별도 보관 권장)
- 갤러리는 **3x3 한 페이지씩** 보이고, **옆으로 넘기면(스와이프)** 다음 9장이 나옵니다.
  하단 점(●)으로 현재 페이지 표시. 한 장을 누르면 전체화면에서 좌우로 넘겨볼 수 있어요.
- 핀치 줌(확대)·길게 눌러 저장은 막혀 있습니다.

### 갤러리 사진을 추가/변경할 때
1. `images/web/` 에 사진 추가 (모바일을 위해 1장 200~400KB 정도로 압축 권장)
   - 압축 예시: `sips -Z 1400 -s formatOptions 66 입력.jpg --out images/web/출력.jpg`
2. `index.html`의 `var GALLERY = [ ... ]` 배열에 **파일명만** 추가/삭제
   - 페이지(3x3)와 점은 배열 기준으로 **자동 생성**됩니다. HTML은 안 건드려도 됨.

> ⚠️ GitHub에 올릴 땐 용량 절약을 위해 **고해상도 원본은 빼고** `images/main.jpg` + `images/web/`만 올리세요.

## 3. 지도 (국회의사당사랑재 — 카카오 퍼가기 지도)
- 카카오맵 '지도 퍼가기 > 이미지 지도' 코드를 반응형으로 넣어둠 (`<div class="kakao-roughmap">`)
- 길찾기 버튼: 카카오맵 · 네이버지도 · 티맵 3개 (티맵은 모바일 앱 설치 시 동작)

### 지도를 다른 장소로 바꾸려면
1. https://map.kakao.com 에서 장소 검색 → '공유' → **지도 퍼가기** → **이미지 지도** → 소스 복사
2. `index.html`의 `<div class="kakao-roughmap">` … `</div>` 부분을 새 소스로 교체
3. 단, 복사한 이미지 주소의 `http://` 를 `https://` 로 바꿔야 깃허브(https)에서 안 깨짐
   (현재 코드는 이미 https로 적용해 둠)

> 참고: 카카오 퍼가기 이미지 주소는 시간이 지나면 만료될 수 있어요.
> 안 보이면 위 과정으로 소스를 다시 받아 교체하세요.

## 4. GitHub에 올리기 (GitHub Pages)
1. GitHub에서 New repository → 이름 예: `wedding` → Public
2. 이 폴더 파일들을 업로드 (웹에서 드래그&드롭 또는 git push)
3. repo → Settings → Pages → Source: `main` 브랜치 / `/ (root)` → Save
4. 1~2분 뒤 `https://본인아이디.github.io/wedding` 으로 접속
5. 그 링크를 카톡/문자로 공유

### git 명령으로 올리는 경우
```bash
cd wedding
git init
git add .
git commit -m "모바일 청첩장"
git branch -M main
git remote add origin https://github.com/본인아이디/wedding.git
git push -u origin main
```
