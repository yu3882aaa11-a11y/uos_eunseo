# CLAUDE.md

## 프로젝트 개요

임재정 개인 Portfolio 사이트. 하위 페이지 없이 한 페이지를 스크롤하며 모든 콘텐츠를 보는 원 페이지 웹사이트다.
상세 요구사항은 `PRD.md`를 따른다. 원본 요구사항은 `docs/Profile_요구사항.txt`.

## 기술 스택

- Frontend: Next.js (App Router) + TypeScript + Tailwind CSS
- Backend: Express + TypeScript (Vercel Functions)
- Database (향후): PostgreSQL (Neon / Supabase) + Prisma — 초기에는 Backend 내 정적 데이터 사용
- 배포: Vercel (Frontend, Backend 각각 별도 프로젝트)

## 폴더 구조

아직 스캐폴딩 전이며, 아래 구조로 만든다.

```
/
├── frontend/   # Next.js 앱
├── backend/    # Express API
└── docs/       # 요구사항, 디자인 참고 자료 (수정하지 않음)
```

## 개발 규칙

- **원 페이지**: 하위 라우트 페이지를 추가하지 않는다. 콘텐츠는 섹션(`#home`, `#about`, `#activities`, `#career`, `#contact`)으로 나누고 앵커 스크롤로 이동한다.
- **FE/BE 분리**: 프로필·활동·경력 데이터는 Frontend에 하드코딩하지 않고 Backend API(`/api/profile`, `/api/activities`, `/api/careers`)에서 조회한다.
- **DB 연동 대비**: Backend의 데이터 접근은 별도 계층으로 분리해, 정적 데이터를 DB로 교체해도 API 응답 형태와 Frontend가 바뀌지 않게 한다.
- **Java 지양**: Java 및 Java 기반 기술(Spring, JSP 등)을 사용하지 않는다.
- **Vercel 배포**: Vercel에서 동작하지 않는 방식(상시 실행 서버 전제, 로컬 파일 쓰기 등)을 쓰지 않는다.
- **TypeScript**: Frontend, Backend 모두 TypeScript로 작성한다.
- **디자인**: Figma 참고 파일의 레이아웃·색상·타이포그래피를 기준으로 한다.
- **환경변수**: Backend 주소 등은 환경변수(`NEXT_PUBLIC_API_URL`)로 주입하고, `.env` 파일은 커밋하지 않는다.

## 명령어

`frontend/`, `backend/` 각 폴더에서 실행한다. 스캐폴딩 후 실제 스크립트에 맞게 갱신한다.

```
npm install     # 의존성 설치
npm run dev     # 개발 서버
npm run build   # 빌드
npm run lint    # 린트
```

## 참고 자료

- 요구사항: `docs/Profile_요구사항.txt`
- 프로필 이미지: `docs/프로필사진.png`
- Figma 원본: `docs/Portfolio (Community).fig`
- Figma URL: https://www.figma.com/design/isMqGYYV6k9IWap1589ORk/Portfolio--Community-?node-id=0-1&p=f&t=47WdNGMriZQpG8xD-0

## 응답 언어

사용자와의 대화 및 문서 작성은 한국어로 한다.
