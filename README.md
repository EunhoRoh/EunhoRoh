# 노은호 (ROH EUNHO)

**풀스택 개발자 · AI 서비스 통합 · QA 자동화** — 요구사항부터 DB·API·화면·서버까지 직접 만들고, 신규 사업 기획까지 맡아 봤습니다.

📧 deu04189@gmail.com · 🌐 [포트폴리오 원페이지](https://eunhoroh.github.io)

---

## 경력 — 테바소프트 SW팀 (2025.01 – 2026.10, 1년 10개월)

초등학생 정서 케어 서비스(사용자 수만 명)와 외주 개발을 하는 회사에서 풀스택 → QA 자동화 → 신규 사업 기획·구현 순으로 맡았습니다.

**Seamspace Family — 신규 사업 기획·프로토타입·운영 저장소 통합·부모앱 React 재구현 (2026.04–09)**
- 기획 담당자가 따로 없어 리서치부터 맡았습니다. 해외 사례·국내 경쟁·법 규제를 조사하고 방향 후보 4안을 비교해 대표 보고서를 썼고, Django + Flutter 프로토타입으로 설계를 검증했습니다
- 경영 결정으로 독립 앱이 기존 서비스의 확장으로 바뀌었을 때 코드가 아니라 검증된 설계를 옮겼습니다. 수만 줄 모놀리스에 `family` 앱을 격리 신설(모델만 로드하는 스텁으로 무거운 임포트 차단, 기존 코드 수정 초기 3줄), 자녀 계정 통합은 서버가 기존 응답에 값을 갈아끼우는 어댑터로 **앱 수정 0**
- 일기 공개범위 3단계를 직렬화 단계에서 강제(비밀 글은 응답에 없음, 남의 것은 404), 부모가 자녀 공개범위를 대신 못 바꾸는 규칙을 회귀 테스트로 고정
- 부모앱을 Flutter → React 18 + TypeScript로 **이틀 만에 전 화면 이식**(62파일 14,475줄 인벤토리 → 58파일 포팅). 제가 만든 가족톡방 2,200여 줄은 폐지하고 기존 기능 재사용
- AI '오늘의 질문'(gpt-4o-mini): 11사례×2회 실측으로 프롬프트 3차 개선 — 안전 판정 2단계 JSON, 모델 호출 전 고위험 규칙 차단. family 테스트 111건
- 대표·개발팀 확인용 사내 테스트 서버에 격리 스택으로 올리는 단계까지 진행(운영 배포 전)하고 인수인계

**Atrion — 건축물 품질관리 시스템 풀스택 (2025.06–12, 외주)**
- 요구사항 → DB 스키마(테이블 약 35개) → API → 화면까지 단독. 대시보드 차트 34개, 슬로우쿼리 복합 인덱스, 루프 안 N+1을 GROUP BY로
- PPT 보고서 자동화를 Celery 비동기로 분리해 실패율 30%→0%, 10초→3초. Azure Custom Vision으로 하자 사진 자동 분류
- 구조 재현 데모: [pptx-report-pipeline-demo](https://github.com/EunhoRoh/pptx-report-pipeline-demo)

**SLM 위기판정 통합 (정부 과제, DICIA·한서대 협력)**
- 협력팀이 학습한 SLM(Qwen2-7B+LoRA)을 학생 일기 서비스 응급 파이프라인에 통합·상용 운영: 감정점수 1차 게이트 → 위험군만 HTTP 분류 → 실패 시 응급 간주(fail-safe) → 13개 언어 핫라인·교사 알림. 누적 2,284건(내부 집계)
- 공인시험 검증 체계 설계: 정확도 산식, 한/영 라벨 동의어 판정 규칙, 재현 절차, SHA-256 고정. ※ 모델 학습·평가는 한서대
- ChatGPT API 기반 AI 성격 챗봇 11종 운영(키 로테이션·aiohttp), 일기·채팅 프롬프트 관리

**QA 자동화 — 학생앱 Flutter E2E·API 자동화 단독 구축 (2025.02–2026.09)**
- TC 1,511건 워크북, 자동화 882건, 시나리오 49개, 15개 언어 회귀. 플레이키는 재시도가 아니라 구조로(데드라인 폴링, 실패 시 자가 복구)
- 프로덕션 무수정으로 XHR을 가로채 request/response를 리포트에 첨부. API 러너(Node, 레시피 90종) 신설
- 9월 한 달 결함 52건을 등급·재현 로그와 함께 기록, 보안·심각 5건 개발팀 전달. 팀원용 웹 테스트 러너 Seam Runner(Node·systemd·Cloudflare Access) 운영

**운영·성능**
- 헬스체크 이중 봇(1분·30분): 소셜 로그인 장애를 사용자 문의에서 **30분 내 자동 탐지**로, 비대칭 타임아웃 설계로 알림 폭주 30~60건→0
- 38,230명 배치가 로그 없이 죽던 문제를 OOM 가설 → 코드 리뷰로 N+1 근본원인 발견 → 재설계 → 운영 배포(2026.07). 같은 패턴 재현: [django-n-plus-one-lab](https://github.com/EunhoRoh/django-n-plus-one-lab) — 쿼리 5,998→11회, 379초→0.24초(데모 실측)

---

## 공개 레포

실무 코드는 외주·사내 자산이라 비공개입니다. 아래는 개인 프로젝트와, 실무 문제의 구조를 더미 데이터로 재현한 데모입니다.

| 레포 | 무엇 | 상태 |
|---|---|---|
| [sealo](https://github.com/EunhoRoh/sealo) | 물범이 알람으로 깨우고 도장을 찍어 주는 루틴 앱. Spring Boot 4.1 + React Native(Expo). N+1을 구조로 예방(핵심 화면 쿼리 2번), FCM 대신 로컬 알림, AI 플랜은 인터페이스 + 룰 엔진 | 2026.07 · API 24개 · 통합 테스트 29건 · 결정로그 27건 |
| [django-n-plus-one-lab](https://github.com/EunhoRoh/django-n-plus-one-lab) | 실무 배치 OOM 장애를 재현한 N+1 실험실, seed/bench로 재측정 가능 | 완성 |
| [pptx-report-pipeline-demo](https://github.com/EunhoRoh/pptx-report-pipeline-demo) | 차트 렌더링 → PPT 조립 → Celery 큐 파이프라인 | 완성 |

---

## 기술

| 구분 | 실무 (테바소프트) | 개인 프로젝트 |
|---|---|---|
| 언어 | Python, JavaScript/TypeScript, Dart, SQL | Java 21, TypeScript |
| 백엔드 | Django REST Framework, Celery | Spring Boot 4.1, JPA, Spring Security |
| 프론트·앱 | React 18 + TypeScript(Vite, TanStack Query), Vue 3, Nuxt, Flutter | React Native(Expo), TanStack Query |
| AI | SLM 서비스 통합, OpenAI API 챗봇·프롬프트 설계, Azure Custom Vision | 생성기 인터페이스 + 룰 엔진(LLM 연결 전) |
| QA·자동화 | Flutter integration_test, Node API 러너, Playwright, 헬스체크 봇 | Spring 통합 테스트(MockMvc) |
| DB·인프라 | PostgreSQL, MySQL, Redis, Docker, Nginx, Cloudflare, systemd | PostgreSQL 16, Docker Compose |

연구: **KCC 2022 제1저자** — CNN-LSTM 심방세동 탐지(정확도 99.45%, AUC 0.99), 모델을 직접 설계·학습·평가. 캡스톤 우수상, 건국대 의료해커톤 결선.
자격: 정보처리기사 · SQLD · OPIc IM2 · TOEIC 815. 한동대학교 AI·컴퓨터공학심화 학사, Vilnius University 교환학생.

AI 페어 프로그래밍을 씁니다. 설계·검증·결정은 제가 하고 결정로그와 회귀 테스트로 남깁니다.
