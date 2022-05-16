# Backend Programming

### 1.1 Server 구성 Use Case

### 1.2 Server의 형태

- Monolithic Architecture : 모든 것을 하나에서 처리
- MSA(Microservice Architecture) : 개별 서버로 구성하고 서로 통신

### 1.3 REST API

- 정보를 주고 받을 때 사용되는 형식
  - CRUD : Create, Read, Update, Delete

### 1.4 HTTP Method

- 정보를 주고 받을 때 지켜야 하는 통신 규약
- GET : 정보를 요청하기 위해 사용(READ)
- POST : 정보를 입력하기 위해 사용(CREATE)
- PUT : 정보를 업데이트하기 위해 사용(UPDATE)
- PATCH : 정보를 업데이트하기 위해 사용(UPDATE)
- DELETE : 정보를 삭제하기 위해 사용(DELETE)

### 1.5 Header와 Body

- Header : 보내는 주소, 받는 주소, 시간
- Body : 실제 전달하려는 내용

### 1.6 Status Code

<img width="500" alt="스크린샷 2022-05-16 오후 10 21 07" src="https://user-images.githubusercontent.com/56240088/168603599-cc29abd1-ce21-4c30-8450-6fd33acf78ea.png">

### 1.7 동기와 비동기

- 동기(Sync) : 서버에서 요청을 보냈을 때, 응답이 돌아와야 다음 동작 수행
- 비동기(Async) : 요청이 보낼 때 응답 상태와 상관없이 다음 동작 수행

### 1.8 IP

 - 네트워크에 연결된 특정 PC 주소를 나타내는 체계
 - Localhost, 127.0.0.1 : 현재 사용 중인 Local PC

### 1.9 Port

 - 0 ~ 1024는 통신을 위한 규약에 정해짐
 - 22 : SSH
 - 80 : HTTP
 - 443 : HTTPS

