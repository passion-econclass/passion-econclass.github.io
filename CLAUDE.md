# CLAUDE.md

이 저장소는 「쓸공언니」(쓸데없이 공부 많이하는 언니들) 홍보 사이트예요. GitHub Pages로 배포하는 정적 사이트예요.
사용자와는 한국어로 대화하고, 사이트 문구도 한국어로 써요.

## 구조

- `index.html`: 사이트 전체(HTML, CSS, JS)가 이 한 파일에 있어요. 빌드 도구와 패키지는 없어요.
- `.nojekyll`: GitHub Pages가 Jekyll 처리를 하지 않게 해요.
- `README.md`: 사용자가 직접 내용을 고치는 방법이에요.
- `WORKLOG.md`: 지금까지의 작업 기록이에요. 의미 있는 변경을 하면 여기에도 추가해요.

## 배포

- 저장소: `passion-econclass/passion-econclass.github.io` (조직 `passion-econclass`). 개인 계정에서 이 조직으로 옮겨 왔어요. 사용자 개인 이름이 드러나지 않게 하려고 옮긴 것이니, 사이트나 문서에 예전 계정 이름과 주소를 쓰지 마세요.
- GitHub Pages: `main` 브랜치, `/ (root)` → https://passion-econclass.github.io/
- 작업 브랜치에 커밋한 뒤, 사용자가 원하면 같은 커밋을 `main`에도 푸시해요. 지금까지는 매번 두 브랜치를 같은 커밋으로 맞춰 왔어요:
  - `git push origin <작업 브랜치>`
  - `git push origin <작업 브랜치>:main`

## 디자인 원칙

사용자가 "너무 번쩍번쩍하다"고 해서 **차분하고 따뜻하며 전문적인** 디자인으로 바꿨어요. 이 방향을 유지해요.

- 네온 그라데이션, 회전·반짝임·흐르는 띠 같은 화려한 애니메이션은 쓰지 않아요. 효과는 스크롤할 때 살짝 나타나는 `.reveal` 정도만 써요.
- 색은 `:root` 변수를 써요: `--bg`(아이보리), `--paper`, `--sand`, `--ink`(짙은 갈색), `--body`, `--muted`, `--line`, `--accent`(테라코타), `--green`(딥그린), `--gold`.
- 제목은 `.serif`(Noto Serif KR), 본문은 Noto Sans KR이에요. 섹션 머리는 `.label` + `.sec-title.serif` + `.sec-sub` 패턴을 써요.
- `section.alt`로 섹션 배경을 번갈아 바꿔요.
- 모바일(390px)에서 가로 스크롤이 생기면 안 돼요.

## 콘텐츠 데이터와 출처

| 항목 | 위치(`index.html`) | 출처 |
|---|---|---|
| 영상 목록 | `<script>`의 `VIDEOS` 배열 `[영상ID, "N화. 제목"]`, 최신이 맨 앞 | https://www.youtube.com/channel/UCtzEc_tO0vJj-hMhgKLOQ3w/videos 페이지 HTML의 `videoId` / `lockupViewModel` |
| 영상 주제 필터 | `CATS` 배열의 정규식 | 제목 키워드로 자동 분류 |
| 숫자 정보 | `.facts` 영역의 `.num` | Apple 팟캐스트 팔로워(37,000+, 사용자 제공: Apple은 공개하지 않음), YouTube 구독자 수, 블로그 이웃 수 |
| 블로그 글 | `#blog` 섹션(대표 글, 글 목록, 경제 수업 노트, 연금 가이드, 거장들에게 배우는 투자) | RSS `https://rss.blog.naver.com/passionchoi55.xml` (최근 50개), 전체 목록 `https://blog.naver.com/PostTitleListAsync.naver?blogId=passionchoi55&currentPage=N&countPerPage=30` |
| 팟캐스트 | `https://podcasts.apple.com/kr/podcast/id1650713547` | iTunes Search API (`itunes.apple.com/search?media=podcast`) |
| Instagram | `#insta` 섹션 카드, `IG_POSTS` 배열 | 사용자가 보낸 캡처 |

- 블로그 글 주소는 `https://blog.naver.com/passionchoi55/글번호` 형태로 써요. RSS 주소에 붙는 `?fromRss=...`는 빼요.
- 블로그 글을 추가할 때는 실제 블로그 제목을 확인해서 써요. 대표 글 카드처럼 디자인상 짧게 줄일 때만 예외예요.
- 강의 문의 메일 `passion.econclass@gmail.com`은 운영자가 Instagram에 공개한 연락처라 사이트에 넣어도 돼요.

## 제약 사항

- **Instagram은 자동으로 가져오지 않아요.** 로그인 없이는 로그인 화면으로 넘어가요. 비공식 API로 가져오려던 시도는 권한 검사에서 거부됐어요. 게시물은 사용자가 준 주소를 `IG_POSTS`에 넣어 공식 퍼가기(embed)로 보여 줘요.
- 작업 환경 네트워크는 허용 사이트만 접속할 수 있어요. 지금 허용된 곳: www.youtube.com, youtube.com, i.ytimg.com, www.instagram.com, itunes.apple.com, podcasts.apple.com, blog.naver.com, rss.blog.naver.com, passion-econclass.github.io(배포 확인용).
- 채널 프로필 이미지(`yt3.googleusercontent.com`)는 작업 환경에서 막혀서 스크린샷에 빈칸으로 나와요. 실제 브라우저에서는 정상이에요.
- 숫자와 영상 목록은 자동으로 바뀌지 않아요. 업데이트를 요청받으면 위 출처에서 다시 가져와요.

## 결정된 사항

- 채널 순서는 중요도 순으로 **팟캐스트 → 유튜브 → 인스타그램 → 블로그**예요. 새 링크나 목록을 넣을 때도 이 순서를 지키고, 강조(primary) 버튼은 팟캐스트예요.
- 영상은 사이트 안에서 재생하지 않고 유튜브로 이동해요(`watch()` 링크). 영상 대부분이 YouTube에서 "퍼가기 허용"이 꺼져 있어 사이트 안 재생이 안 되기 때문이에요. 퍼가기 상태는 `https://www.youtube.com/embed/영상ID` HTML의 `previewPlayabilityStatus`로 확인할 수 있어요.
- 소개 제목 "쓸데 없을 만큼 깊게 공부하고, 쓸모 있을 만큼 쉽게 전합니다"의 "쓸데 없을" 띄어쓰기는 대구를 위해 일부러 띄운 거예요. 맞춤법에 맞춰 붙이지 마세요.
- 사이트에 "US CPA" / "미국회계사 진행" 표기를 넣지 않아요(사용자 요청). 소개 문장의 "미국회계사 언니들"은 채널 소개 문구라 남아 있어요.
- 팟빵 접속 허용은 사용자가 거절했어요. 팟캐스트 숫자는 사용자에게 물어봐요.
- 진행자 소개에는 **최열정** 님만 넣어요. 팟캐스트에는 정관리 님도 진행자로 나오지만, 사용자가 추가하지 않기로 했어요.
- 하워드 막스 글(223997577523)은 블로그 대표 글과 「거장들에게 배우는 투자」 두 곳에 들어가 있어요. 사용자가 바꾸자고 하지 않았어요.
- 'CMA·ISA·IRP 한눈에!' 글은 IRP를 다뤄서 연금 가이드 3층(개인연금)에 넣었어요.

## 확인 방법

변경한 뒤에는 Playwright로 데스크톱(1280px)과 모바일(390px) 화면을 찍어서 확인해요:

- 페이지 오류(`pageerror`)가 없어야 해요.
- `document.documentElement.scrollWidth`가 화면 너비와 같아야 해요(가로 스크롤 없음).
- 스크린샷을 찍기 전에 `.reveal` 요소에 `in` 클래스를 붙여야 내용이 보여요.
- 스크린샷은 저장소가 아니라 스크래치 폴더에 저장해요.

## 커밋

- 커밋 메시지는 영어로, 무엇을 바꿨는지 짧게 써요.
- 사이트 내용이 바뀌면 `README.md`(수정 방법)와 `WORKLOG.md`(작업 기록)가 지금 상태와 맞는지 확인해요.
