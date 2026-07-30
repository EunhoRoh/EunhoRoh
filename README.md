# 노은호 (ROH EUNHO)

**백엔드 엔지니어** — 실무 Django · 개인 프로젝트 Spring Boot, QA 자동화와 운영 신뢰성까지 커버 | 테바소프트 SW팀

📧 deu04189@gmail.com · 🌐 [포트폴리오 원페이지](https://eunhoroh.github.io)

---

## 📊 한눈에 보는 핵심 수치

| 영역 | 수치 | 근거 |
|---|---|---|
| PPT 보고서 자동화 (실무) | 실패율 **30%→0%** · 생성 **10초→3초** | Celery 큐 워커 분리 — 구조는 데모 레포로 재현 |
| 모니터링 대시보드 (실무) | 차트 **34개** UI+API 풀스택 | Vue/Nuxt + Django REST |
| QA 자동화 (실무) | TC **1,005건** 워크북 운영 · **405건** 자동화 | Flutter E2E 단독 구축 — 시나리오 43개 · 11개 언어 회귀 |
| 운영 장애 탐지 (실무) | 수동 인지→**30분** 자동 탐지 · 알림 **30~60건→0** | 이중 봇 헬스체크 + OAuth 검증 봇 |
| N+1 쿼리 최적화 | 쿼리 **5,998→11** · **379초→0.24초** (데모 실측) | 실무 최적화 배치는 **운영 배포 완료(2026.07)** — 동일 패턴 더미 재현 |

---

## 💼 경력 요약 — 테바소프트 SW팀 (2025.01~현재, 1년 7개월차)

풀스택(Django+Vue) → QA 자동화 → 운영 신뢰성 순으로 역할을 넓혀 왔습니다.

**PPT 보고서 자동 생성 파이프라인 (건축물 품질관리 시스템 외주, 2025.06~12)**
- 문제: 요청-응답 안에서 차트 렌더링+PPT 조립 → 타임아웃으로 실패율 30%
- 결정: 서버측 차트 렌더링(Chart.js + html-to-image) + Celery 큐 워커 분리로 결정적(deterministic) 생성 경로 확보
- 결과: 실패율 30%→0%, 생성시간 10초→3초. 대시보드 차트 34개(신규 13 + 리디자인 21)와 고객 피드백 페이지(DB 스키마→API→UI)를 단독 풀스택 개발
- 파이프라인 구조는 [pptx-report-pipeline-demo](https://github.com/EunhoRoh/pptx-report-pipeline-demo)로 공개 (데모는 같은 구조를 matplotlib로 재현)

**서비스 헬스체크 모니터링 (2025.03~, 운영·신뢰성)**
- 문제: 피크시간 Celery 적체 시 "느리다"만 알고 실제 응답시간 측정 불가 + 알림 30~60건 폭주. 과거 `.env` 설정 누락으로 구글 로그인 전체 장애를 사용자 문의로만 인지
- 결정: 타임아웃 12초 유지 + 초과 시 백그라운드 스레드로 측정 인계(비대칭 설계), Google OAuth refresh_token 기반 30분 주기 자동 검증 봇 신설
- 결과: 실제 응답시간 정량 측정 + 알림 폭주 제거, 소셜 로그인 장애 탐지 리드타임을 사용자 문의 의존에서 30분 이내로 단축

**QA 자동화 & 성능 최적화 (2025.03~현재, 주 업무)**
- Flutter 기반 E2E 자동화를 단독 구축 — QA 워크북 TC 1,005건 운영, 405건 자동화 완료(+101건 구현 중). Robot(POM) 패턴 + 시나리오 43개, 전체 회귀 약 19분, 브라우저 XHR을 가로챈 request/response 재현 리포트 자동 첨부. 팀 초기 자동화 틀(Playwright·Appium·GitHub Actions 스캐폴드, 2025.02)도 구축
- 38,230명 뱃지 배치가 로그 없이 절반에서 중단 → OOM 추론 → N+1(유저별 행성 전체 재쿼리) 근본원인 발견 → 행성별 1회 쿼리 + status_map 사전 판정 + iterator(chunk_size=500)로 재설계, **최적화 버전 운영 배포 완료(2026.07)**
- 같은 패턴을 더미 데이터로 재현해 실측: [django-n-plus-one-lab](https://github.com/EunhoRoh/django-n-plus-one-lab) — 쿼리 5,998→11회, 실행시간 379초→0.24초(약 1,580배 단축), 피크 메모리 6.3→0.7MB. seed/bench 커맨드로 누구나 재측정 가능

---

## 📂 공개 레포 가이드

실무 코드는 외주·사내 자산으로 비공개입니다 — 아래는 그 구조를 더미 데이터로 재현한 데모와 개인 풀스택 프로젝트입니다.

**[sealo](https://github.com/EunhoRoh/sealo)** — 물범이 도장을 쾅 찍어주는 루틴 앱, Spring Boot 4.1/Java 21 + RN(Expo) 1인 풀스택
- 핵심: 알람→도장→조개 보상→물범 꾸미기 리텐션 루프 (iOS·Android·Web 단일 코드) · N+1 예방 구조화 · 통합 테스트 29건
- 상태: 진행 중 (알람~AI 플랜·집중 모드까지 동작, 실기기 검증 단계)

**[django-n-plus-one-lab](https://github.com/EunhoRoh/django-n-plus-one-lab)** — 실무 배치 OOM 장애를 더미 데이터로 재현한 N+1 실험실
- 핵심: seed/bench 커맨드로 벤치 재측정 가능
- 상태: 완성

**[pptx-report-pipeline-demo](https://github.com/EunhoRoh/pptx-report-pipeline-demo)** — 차트 렌더링→PPT 조립→Celery 큐 파이프라인
- 핵심: 문제→결정→근거 표 · 동기/비동기 실행 가능
- 상태: 완성

**[Itda](https://github.com/EunhoRoh/Itda)** — 끊어진 인연에 다시 연락할 용기를 주는 관계 회복 앱, Spring Boot 4.1 + RN(Expo)
- 핵심: '오늘의 한 사람' 추천 → 추억 기록 → 4단계 재연락 미션 (심리학 RCT 연구 근거). 위험 관계는 서버가 미션 생성을 거부(409, 테스트 검증)
- 상태: MVP (핵심 루프 구현 · 테스트 11건 통과 · AI 양측 개별 상담 중재는 설계 로드맵)

---

## 🛠 기술 스택

| 구분 | 실무 (테바소프트) | 개인 프로젝트 |
|---|---|---|
| 언어 | Python, JavaScript/TypeScript, Dart, SQL | Java 21, TypeScript |
| 백엔드 | Django, Django REST Framework, Celery | Spring Boot 4.x (JPA, Spring Security) |
| 프론트/모바일 | Vue.js 3, Nuxt.js, Flutter | React Native(Expo), TanStack Query, React/Next.js(학습) |
| AI/ML | OpenAI API 프롬프트 설계, Azure Custom Vision 연동 | LLM 플랜 아키텍처 설계 (룰 엔진 v1로 선검증) |
| QA/자동화 | Playwright, Flutter integration_test, API 헬스체크 봇(Telegram) | — |
| DB/인프라 | PostgreSQL, MySQL, Redis, Docker, Nginx, Cloudflare, NCP | PostgreSQL 16 (Docker Compose), AWS EC2/RDS(학습) |

---

## 🎓 연구·논문·자격

- **KCC 2022 제1저자** — "CNN-LSTM을 활용한 심방세동 탐지" (정확도 99.45%, 민감도 99.75%, AUC 0.99), 한국정보과학회
- 한동대 캡스톤 디자인 경진대회 우수상 (2022.06) · 건국대 의료 해커톤 결선 (2021.10)
- 정보처리기사 (2024.09) · SQLD (2023.10)
- OPIc IM2 (2026.01) · TOEIC 815
- 한동대학교 AI·컴퓨터공학심화 학사 · Vilnius University(리투아니아) 교환학생

---

📧 **deu04189@gmail.com**
