# 쓸공언니 홍보 사이트

쓸데없이 공부 많이하는 언니들. 미국회계사 언니들이 들려주는 국제 경제 뉴스와 경제·투자 책 이야기.

- YouTube: https://www.youtube.com/channel/UCtzEc_tO0vJj-hMhgKLOQ3w
- Instagram: https://www.instagram.com/passion.econclass
- Blog: https://blog.naver.com/passionchoi55
- Podcast: https://podcasts.apple.com/kr/podcast/id1650713547

## GitHub Pages로 배포하기

1. 저장소 **Settings → Pages** 로 이동
2. **Source**: `Deploy from a branch`
3. **Branch**: `main` 과 `/ (root)` 를 선택하고 **Save**
4. 1~2분 뒤 `https://passion-econclass.github.io/` 에서 확인

## 내용 수정하기

모든 내용은 `index.html` 한 파일에 있어요.

- **새 영상 추가**: `<script>` 안의 `VIDEOS` 배열 맨 앞에 `["영상ID", "208화. 제목"]` 을 추가하세요.
  영상 ID는 유튜브 주소 `watch?v=` 뒤의 11글자예요. 첫 번째 영상이 자동으로 "최신" 대표 영상이 돼요.
- **숫자(구독자·에피소드·이웃 수)**: `class="facts"` 영역의 `<div class="num">` 안 숫자를 바꾸세요.
- **블로그 글 / 인스타 카드**: `#blog`, `#insta` 섹션의 텍스트와 링크를 바꾸세요.
  블로그 글 주소는 `https://blog.naver.com/passionchoi55/글번호` 형태예요.
- **인스타그램 게시물 연결**: `<script>` 안의 `IG_POSTS` 배열에 게시물 주소를 넣으세요.
  예: `const IG_POSTS = ["https://www.instagram.com/p/ABCdef123/", ...];`
  주소를 넣으면 Instagram 공식 퍼가기(embed)로 실제 게시물이 보이고, 비워 두면 기존 카드 디자인이 보여요.

작업 내역은 `WORKLOG.md` 에 정리되어 있어요.
