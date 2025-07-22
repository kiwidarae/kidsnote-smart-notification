# 키즈노트 스마트 알림 서비스

> 키즈노트의 중요한 알림을 자동으로 감지하여 텔레그램으로 알려주는 서비스

## 📋 프로젝트 개요

### 목적
- 키즈노트 알림장/공지사항에서 준비물, 중요 일정 자동 감지
- LangChain/LangGraph를 활용한 AI 기반 중요도 분석
- 텔레그램을 통한 즉시 알림으로 놓치는 일 방지

### 핵심 기능
- [x] ✅ 새 게시물 자동 감지 (크롤링)
- [x] 🤖 AI 기반 중요도 판단 (LangChain)
- [x] 📱 텔레그램 즉시 알림
- [x] 🔄 완전 자동화 (사용자 개입 최소화)

## 🛠️ 기술 스택

### Backend
- **Python 3.13.5: 메인 개발 언어
- **LangChain**: AI 체인 구축
- **LangGraph**: 워크플로우 관리
- **Selenium**: 웹 크롤링
- **FastAPI**: API 서버 (Azure 배포 시)

### AI & ML
- **OpenAI GPT**: 텍스트 분석 (또는 로컬 LLM)
- **Prompt Engineering**: 중요도 판단 로직

### Infrastructure
- **Azure Functions**: 주기적 크롤링 (서버리스)
- **Azure App Service**: FastAPI 호스팅 (무료 티어)
- **Telegram Bot API**: 알림 발송

### Development
- **GitHub**: 코드 및 문서 관리
- **로컬 개발**: 초기 개발 및 테스트

## 📁 프로젝트 구조

```
kidsnote-smart-notification/
├── README.md                   # 이 파일
├── docs/                      # 문서
│   ├── development-log.md     # 개발 일지
│   ├── setup-guide.md         # 환경 설정 가이드
│   ├── deployment.md          # 배포 가이드
│   └── api-reference.md       # API 문서
├── src/                       # 소스 코드
│   ├── crawler/              # 크롤링 모듈
│   │   ├── __init__.py
│   │   ├── kidsnote_crawler.py
│   │   └── utils.py
│   ├── analyzer/             # AI 분석 모듈
│   │   ├── __init__.py
│   │   ├── langchain_analyzer.py
│   │   ├── prompts.py
│   │   └── workflows.py
│   ├── notification/         # 알림 모듈
│   │   ├── __init__.py
│   │   ├── telegram_bot.py
│   │   └── message_templates.py
│   └── main.py              # 메인 실행 파일
├── azure/                    # Azure 배포용
│   ├── functions/           # Azure Functions
│   └── app-service/         # App Service 설정
├── config/                   # 설정 파일
│   ├── settings.py
│   └── prompts.yaml
├── tests/                    # 테스트 코드
├── requirements.txt          # Python 의존성
├── .env.example             # 환경변수 예시
├── .gitignore               # Git 무시 파일
└── LICENSE                  # 라이선스
```

## 🎯 개발 로드맵

### Phase 1: 로컬 개발 (1-2주)
- [ ] 개발 환경 설정
- [ ] 키즈노트 크롤링 구현
- [ ] 텔레그램 봇 연동
- [ ] 기본 키워드 분석

### Phase 2: AI 분석 (1-2주)  
- [ ] LangChain 기본 체인 구현
- [ ] LangGraph 워크플로우 설계
- [ ] 프롬프트 엔지니어링
- [ ] 중요도 판단 로직 고도화

### Phase 3: 통합 및 테스트 (1주)
- [ ] 전체 파이프라인 연결
- [ ] 실제 키즈노트 데이터로 테스트
- [ ] 에러 처리 및 안정성 향상

### Phase 4: Azure 배포 (1주)
- [ ] Azure Functions로 크롤링 이전
- [ ] App Service에 API 배포
- [ ] 환경변수 설정 및 보안
- [ ] 운영 모니터링 설정

## 🚀 빠른 시작

### 1. 저장소 클론
```bash
git clone https://github.com/kiwidarae/kidsnote-smart-notification.git
cd kidsnote-smart-notification
```

### 2. 가상환경 설정
```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. 환경변수 설정
```bash
cp .env.example .env
# .env 파일을 열어서 필요한 값들 입력
```

### 4. 테스트 실행
```bash
python src/main.py
```

## 📚 문서

- [개발 일지](docs/development-log.md) - 개발 과정 기록
- [환경 설정 가이드](docs/setup-guide.md) - 개발환경 구축
- [배포 가이드](docs/deployment.md) - Azure 배포 방법
- [API 문서](docs/api-reference.md) - API 사용법
