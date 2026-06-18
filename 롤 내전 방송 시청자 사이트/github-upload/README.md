# 다비도 내전 · 시청자 라운지 (Viewer Lounge)

치지직 롤 내전 방송 시청자용 페이지 — **내전 배팅 / 내전 상점 / 미니게임**.
미래지향 홀로그램 테마. 포인트·보유 아이템은 브라우저(localStorage)에 저장됩니다.

## 📂 파일 구성

| 파일 | 용도 |
|---|---|
| `davido-inhouse-viewer.html` | **자체 실행 단일 파일.** 더블클릭하면 브라우저에서 바로 열림. 호스팅/GitHub Pages 배포용. |
| `davido-inhouse.dc.html` | **편집용 소스.** 디자인·로직을 여기서 수정. |
| `support.js` | 위 소스를 실행하는 런타임. `davido-inhouse.dc.html`과 **같은 폴더**에 있어야 함. |

## ▶ 바로 보기
`davido-inhouse-viewer.html` 을 브라우저로 열면 끝. (인터넷 없이도 동작)

## ✏️ 수정하는 법
1. `davido-inhouse.dc.html` 을 편집기로 엽니다.
2. 파일 안은 두 부분으로 나뉩니다:
   - `<x-dc> … </x-dc>` — **화면(마크업)**. 색/문구/레이아웃을 인라인 style로 직접 수정.
   - `<script data-dc-script> class Component … </script>` — **로직**. 배당 계산, 상점 가격, 미니게임 규칙 등.
3. 같은 폴더의 `support.js` 와 함께 로컬 서버로 열어 확인합니다.
   예: 폴더에서 `npx serve` 실행 → `davido-inhouse.dc.html` 접속.
4. 수정이 끝나면 `davido-inhouse-viewer.html`(단일 파일)을 다시 만들어 배포하면 됩니다.

## 🔧 자주 바꾸는 값 (davido-inhouse.dc.html 안)
- **상점 가격** — `shopDefs` 배열: 선참권 60 / 노밴권 120 / 종일권 230 / 연장권 300.
- **최대 배팅 / 시작 포인트** — 파일 상단 `data-props` 의 `maxBet`(기본 20), `startingPoints`(기본 100).
- **팀·로스터** — `this.MATCHES` 배열.
- **미니게임 보상/비용** — 슬롯 `cost=5`, 룰렛 배율, 카드 보상 `+30P`, 블랙잭 등.

## ⬆️ GitHub 에 올리기
브라우저: 레포 → **Add file → Upload files** 로 이 폴더의 파일들을 드래그 → Commit.
또는 로컬에서:
```
git add .
git commit -m "Add inhouse viewer lounge"
git push
```

## ⚠️ 참고
- 지금은 **디자인·동작 시안**입니다. 포인트는 각자 브라우저에만 저장돼요(공용 서버 X).
- 치지직 채팅 연동·공용 포인트로 확장하려면, 기존 Next.js 앱의 API(SSE)에 배팅/상점 엔드포인트를 추가해 `support.js` 의 localStorage 부분을 서버 호출로 바꾸면 됩니다.
- 텍사스 홀덤은 "준비중" 상태입니다.
