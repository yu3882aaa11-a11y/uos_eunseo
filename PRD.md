# PRD: 임재정 개인 Portfolio 사이트

> 원본 요구사항: `docs/Profile_요구사항.txt`

## 1. 개요

서울시립대학교 경영학부 임재정의 개인 Portfolio 웹사이트를 개발한다.
방문자(채용 담당자, 동아리·프로젝트 관계자 등)가 한 페이지 안에서 스크롤만으로 자기소개, 활동내역, 수상·경력, 연락처를 모두 확인할 수 있어야 한다.

## 2. 목표 / 비목표

### 목표

- 하위 페이지 이동 없이 하나의 긴 페이지에서 모든 콘텐츠를 보여주는 원 페이지(One Page) 사이트
- Frontend / Backend를 분리한 구조로 개발하고 Vercel에 배포
- 향후 Database 연동이 가능한 구조 (단순 정적 HTML 불가)

### 비목표 (초기 범위 밖)

- 로그인 / 회원 기능
- 관리자(콘텐츠 편집) 페이지
- 실제 Database 연동 (구조만 대비하고 초기에는 Backend 내 정적 데이터 사용)
- 다국어 지원

## 3. 콘텐츠

### 3.1 개인정보

| 항목 | 내용 |
|---|---|
| 이름 | 임재정 |
| 학교 | 서울시립대학교 |
| 전공 | 경영학부 |
| 학번 | 199526000 |
| Tel | 010-0000-0000 |
| E-Mail | limjj157@naver.com |

### 3.2 자기소개

> 안녕하세요!
> 서울시립대학교에서 경영학을 전공 중인 95학번 임재정 입니다.
> 데이터 분석과 MIS에 관심이 많아 시경연에서 2기 회장으로 활발히 활동하고 있습니다.
> 긍정적인 에너지와 논리적 사고로 팀의 성장을 돕는 인재입니다!!

### 3.3 학교 활동내역

- 시립대경영정보연구회 2기 회장
- 중앙 동아리 연극반 10기 연출 담당
- 경영학부 학생회 부회장
- 경영학부 사람사랑 소모임 창립멤버

### 3.4 주요 수상 및 외부 경력

| 내용 | 기간 |
|---|---|
| (주)원스텝 인턴 | 2025.01 ~ 2025.07 |
| 2025 KOICA 글로벌 서포터즈 참여 | 2025.08 |
| 2026 서울시립대학교 해커톤 경진대회 3위 입상 | 2026.07 |
| 대한민국 모두의 창업 2기 프로젝트 지원 | 2026.09 |

## 4. 화면 구성

단일 스크롤 페이지이며, 위에서 아래로 다음 섹션을 배치한다.

| 순서 | 섹션 | 앵커 | 내용 |
|---|---|---|---|
| 1 | Hero | `#home` | 프로필 사진, 이름, 한 줄 소개 |
| 2 | About | `#about` | 자기소개, 학교 / 전공 / 학번 |
| 3 | Activities | `#activities` | 학교 활동내역 |
| 4 | Awards & Career | `#career` | 주요 수상 및 외부 경력 (기간 순 타임라인) |
| 5 | Contact | `#contact` | Tel, E-Mail |

- 상단 고정 내비게이션: 메뉴 클릭 시 해당 섹션으로 부드럽게 스크롤 (페이지 이동 없음)

## 5. 디자인 참고

- Figma: https://www.figma.com/design/isMqGYYV6k9IWap1589ORk/Portfolio--Community-?node-id=0-1&p=f&t=47WdNGMriZQpG8xD-0
- Figma 원본 파일: `docs/Portfolio (Community).fig`
- 프로필 이미지: `docs/프로필사진.png`

위 Figma 디자인의 레이아웃·색상·타이포그래피를 기준으로 하되, 콘텐츠는 3장의 내용으로 대체한다.

## 6. 기능 요구사항

| ID | 요구사항 |
|---|---|
| F-1 | 5개 섹션을 하나의 페이지에 순서대로 렌더링한다 |
| F-2 | 내비게이션 메뉴 클릭 시 해당 섹션으로 앵커 스크롤한다 |
| F-3 | 모든 콘텐츠 데이터(프로필, 활동, 경력)는 Backend API에서 조회한다 |
| F-4 | 데스크톱 / 태블릿 / 모바일 화면에 대응한다 (반응형) |
| F-5 | E-Mail, Tel은 각각 `mailto:`, `tel:` 링크로 제공한다 |
| F-6 | API 조회 실패 시 사용자에게 오류 상태를 표시한다 |

## 7. 비기능 요구사항

| ID | 요구사항 |
|---|---|
| N-1 | Frontend와 Backend는 분리된 프로젝트로 개발한다 |
| N-2 | Frontend, Backend 모두 Vercel에 배포 가능해야 한다 |
| N-3 | 향후 Database 연동 시 Frontend 수정 없이 Backend의 데이터 소스만 교체할 수 있어야 한다 |
| N-4 | Java 및 Java 기반 기술은 사용하지 않는다 |
| N-5 | 단순 정적 HTML 형태로 개발하지 않는다 |

## 8. 기술 스택 / 아키텍처

| 영역 | 기술 | 선정 이유 |
|---|---|---|
| Frontend | Next.js (App Router) + TypeScript + Tailwind CSS | Vercel 기본 지원, 원 페이지 섹션 구성에 적합 |
| Backend | Express + TypeScript (Vercel Functions) | Frontend와 언어 통일, Vercel 배포 가능 |
| Database (향후) | PostgreSQL (Neon 또는 Supabase) + Prisma | Vercel 연동 용이 |
| 배포 | Vercel (Frontend, Backend 각각 별도 프로젝트) | 요구사항 |

```
[Browser] ──> [Frontend: Next.js @ Vercel] ──HTTP/JSON──> [Backend: Express @ Vercel] ──> [정적 데이터 → (향후) PostgreSQL]
```

### 폴더 구조

```
/
├── frontend/   # Next.js 앱
├── backend/    # Express API
└── docs/       # 요구사항, 디자인 참고 자료
```

### API 초안

| Method | Path | 설명 |
|---|---|---|
| GET | `/api/profile` | 개인정보 + 자기소개 |
| GET | `/api/activities` | 학교 활동내역 목록 |
| GET | `/api/careers` | 주요 수상 및 외부 경력 목록 |

- Backend는 Frontend 도메인에 대해 CORS를 허용한다.
- Frontend는 Backend 주소를 환경변수(`NEXT_PUBLIC_API_URL`)로 주입받는다.

## 9. 데이터 모델 초안

향후 Database 테이블 기준. 초기에는 동일한 형태의 정적 데이터를 Backend에 둔다.

**Profile**

| 필드 | 타입 | 비고 |
|---|---|---|
| id | number | PK |
| name | string | 이름 |
| school | string | 학교 |
| major | string | 전공 |
| studentId | string | 학번 |
| tel | string | 연락처 |
| email | string | 이메일 |
| introduction | string | 자기소개 |
| imageUrl | string | 프로필 사진 경로 |

**Activity**

| 필드 | 타입 | 비고 |
|---|---|---|
| id | number | PK |
| title | string | 활동 내용 |
| sortOrder | number | 표시 순서 |

**Career**

| 필드 | 타입 | 비고 |
|---|---|---|
| id | number | PK |
| title | string | 수상 / 경력 내용 |
| startDate | string | 시작 (YYYY.MM) |
| endDate | string \| null | 종료 (YYYY.MM), 단일 시점이면 null |
| sortOrder | number | 표시 순서 |

## 10. 마일스톤

| 단계 | 내용 |
|---|---|
| M1 | `frontend/`, `backend/` 프로젝트 스캐폴딩 |
| M2 | Backend API 3종 구현 (정적 데이터) |
| M3 | Frontend 5개 섹션 구현 및 API 연동 |
| M4 | Figma 디자인 반영, 반응형 처리 |
| M5 | Vercel 배포 (Frontend / Backend) |
| M6 (향후) | Database 연동 |

## 11. 미결 사항

- `.fig` 파일은 Figma 외 도구에서 직접 열 수 없으므로, 세부 디자인 확인을 위해 Figma URL 접근 또는 화면 캡처가 필요하다.
- 학번, 전화번호 등 개인정보의 공개 범위 (현재 전화번호는 `010-0000-0000` 임시값).
- 자기소개의 "95학번"과 학번 `199526000` 표기의 최종 확인.
