# 노은호

백엔드 개발자입니다. 서비스를 직접 만들어 운영하고, 운영하다 생긴 문제는 원인까지 찾아 고칩니다.

- 포트폴리오: https://eunhoroh.github.io
- 이메일: deu04189@gmail.com

## 경력

**테바소프트 SW팀** (2025.01 ~ 2026.10, 1년 10개월)

초등학생 일기 서비스와 외주 시스템을 개발하는 회사에서 백엔드, 화면 개발, AI 기능 연동, QA 자동화를 맡았습니다.

- 사용자 3만 8천 명의 레벨 승급을 계산하다 멈추던 배치의 N+1 문제를 고쳐 DB 조회를 38,230회에서 5~6회로 줄였습니다.
- 구글 로그인 장애를 사용자보다 먼저 알아내는 모니터링 봇을 Python과 Docker로 만들어 운영했습니다.
- 협력 대학이 학습한 SLM 모델을 학생 일기 서비스에 HTTP API로 연동했습니다. 모델이 응답하지 않아도 위험한 일기를 놓치지 않게 설계했고, 누적 2,284건을 처리했습니다.
- GPT가 만든 부모용 질문을 코드로 한 번 더 검사하는 단계를 넣었습니다. 일기 속 내용이 그대로 나오면 다시 생성하고, 일기를 봤다는 표현이 있으면 내보내지 않습니다. 자해, 학대 같은 위험 일기 5건은 테스트에서 모두 막았습니다.
- 일기 분석 프롬프트(12종)와 채팅 프롬프트(6종)를 관리하며, 영어 일기의 감정이 늘 '보통'으로 나오던 문제와 모델이 응급 전화번호를 지어내던 문제를 고쳤습니다.
- 외주 건축물 하자 관리 시스템의 관리자 대시보드 화면(Vue.js, Nuxt.js)과 일부 집계 API를 개발했습니다.
- 학생앱 테스트 케이스 1,511건 중 882건을 자동화했습니다.

## 개인 프로젝트

**다시잇다** (2026.07 ~ 현재, 1인 개발과 운영, 저장소 비공개)

오래 연락이 끊긴 사람과의 관계를 다시 잇도록 돕는 앱입니다. Spring Boot 4.1과 Java 21로 REST API 194개를 만들었고, NCP 서버에 Docker Compose로 배포해 운영하고 있습니다. JWT 토큰 회전, 카카오와 구글 로그인 서버 검증, 테스트 310건과 GitHub Actions CI를 갖췄습니다. Claude Code로 개발하면서 작업 규칙 문서와 결정 기록으로 AI가 쓴 코드를 관리합니다.

## 공개 저장소

| 저장소 | 내용 |
|---|---|
| [sealo](https://github.com/EunhoRoh/sealo) | Spring Boot와 React Native로 만든 루틴 관리 앱 (REST API 24개, 통합 테스트 29건) |
| [django-n-plus-one-lab](https://github.com/EunhoRoh/django-n-plus-one-lab) | 회사에서 겪은 배치 N+1 문제를 더미 데이터로 재현하고 측정한 저장소 |

회사 코드는 비공개라, 공개 저장소에는 실무에서 겪은 문제의 구조만 새로 재현했습니다.

## 기술

- 회사에서 쓴 기술: Python, Django REST Framework, Celery, PostgreSQL, MySQL, Redis, Vue.js, Nuxt.js, React, TypeScript, Flutter, Docker, Nginx, OpenAI API
- 개인 프로젝트: Java 21, Spring Boot 4.1, JPA, Flyway, React Native, Docker Compose, Claude API, GitHub Actions

## 학력과 자격

- 한동대학교 AI·컴퓨터공학심화 졸업, Vilnius University 교환학생
- 정보처리기사, SQLD, OPIc IM2, TOEIC 815
- KCC 2022 제1저자 (CNN-LSTM 심방세동 탐지 모델, 정확도 99.45%)
