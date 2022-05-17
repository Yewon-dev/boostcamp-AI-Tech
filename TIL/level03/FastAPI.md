# FastAPI

### 특징

- Node.js, go와 대등한 성능
- Flask와 비슷한 구조
- Swagger 자동 생성
- Pydantic 을 이용한 Serialization



### 장점

- Flask보다 간결한 Router 문법
- Asynchronous(비동기) 지원
- Built-in API Documentation
- Pydantic을 이용한 Serialization 및 Validation



### 아쉬운 점

- ORM 등 Database와 관련된 라이브러리가 적음



---

### 환경 설정

- poetry라는 가상 환경 및 의존성 관리 소개



### 프로젝트 구조

- 프로젝트의 코드가 들어갈 모듈 설정(app)
- \__main.py__ : 간단하게 애플리케이션을 실행할 수 있는 Entrypoint 역할
  - Entrypoint : 프로그래밍 언어에서 최상위 코드가 실행되는 시작점
- main.py : FastAPI의 애플리케이션과 Router 설정
- model.py : ML model에 대한 클래스와 함수 정의



### Poetry

- Dependency Resolver로 복잡한 의존성들의 버전 충돌 방지
- pyproject.toml 을 기준으로 여러 툴들의 config를 명시적으로 관리
- Poetry 사용 흐름
  - 프로젝트 init
  - Poetry shell 활성화
  - Poetry install
  - Poetry Add



1. 프로젝트 설정하기

   - Fastapi, uvicorn 패키지 설치
   - `source $HOME/.poetry/env`
   - poetry.lock : writing lock file에 생성되는 파일, 작성하고 있는 프로젝트 의존성과 동일한 의존성을 가질 수 있음
   - localhost:8000/docs
   - localhost:8000/redoc

   

2. Swagger

   - 만든 API를 클라이언트에서 호출하는 경우 사용
   - API 디자인
   - API 빌드
   - API 문서화
   - API 테스팅



------

# 기본 지식

### 1.1 Path Parameter

- `/users/402`
- Resource를 식별해야 하는 경우

### 1.2 Query Parameter

- `/users?id=402`
- Query string
- Key, Value의 쌍으로 이루어지며 &로 연결
- 정렬, 필터링을 해야 하는 경우

### 1.3 Optional Parameter

- query가 있으면 출력

### 1.4 Request Body

- 클라이언트에서 API에 데이터를 보낼 때, Request Body를 사용함
- Request Body에 데이터를 보내고 싶으면 POST Method 사용

### 1.5 Response Body

- Output Data를 해당 정의에 맞게 변형
- swagger에 자동으로 문서화

### 1.6 Form, File


-----

## Pydantic

### 2.1 Pydantic

### 2.2 Pydantic Validation

### 2.3 Pydantic Config
