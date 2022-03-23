# Docker

**가상화**

- 개발(Local)과 운영(Production) 서버의 환경 불일치 해소
- 개발 외에 Research도 동일한 환경을 사용할 수 있음



**Docker Image**

- 컨테이너를 실행할 때 사용할 수 있는 템플릿
- Read Only



**Docker Container**

- Docker Image를 활용해 실행된 인스턴스
- Write 가능



## Docker 설치

**홈페이지에서 OS에 맞는 Docker Download**

<img width="600" alt="스크린샷 2021-01-11 오후 11 10 57" src="https://user-images.githubusercontent.com/56240088/154324075-9bd45507-7dce-4f66-81aa-c4807c36e2f4.png">

<img width="600" alt="스크린샷 2021-01-11 오후 11 20 13" src="https://user-images.githubusercontent.com/56240088/154324170-b907651d-54d3-4165-bece-e8c9cfbf3037.png">


**Docker 확인**

<img width="682" alt="스크린샷 2022-02-17 오전 1 40 13" src="https://user-images.githubusercontent.com/56240088/154324215-59c2cbe7-3c32-4f3f-b437-0ac29519aa95.png">


**image 다운받기**

```bash
docker pull [이미지 이름:태그]
```

**다운받은 image 확인**

```bash
docker images
```

<img width="682" alt="스크린샷 2022-02-17 오전 1 44 14" src="https://user-images.githubusercontent.com/56240088/154324359-f336a681-05f9-4dda-827b-02eeb8dcbab9.png">


**다운받은 image를 기반으로 docker container 만들고 실행**

```bash
docker run --name [컨테이너 이름] -e [환경변수 설정] -d -p [포트 지정] [image]
```

- -e : Set environment variables
- -d : 데몬(백그라운드) 모드
- -p : Publish a container's port(s) to the host

```bash
# 폴더를 마운트해서 이미지 실행
docker run -i -t -v [윈도우의 폴더]:[컨테이너의 폴더] [이미지 이름]:[태그 이름]
```

- -v : Bind mount a volume
- -i : Keep STDIN open even if not attached
- -t : Allocate a pseudo-TTY

> 이전에 간단하게 정리해둔 [자료 참고](https://github.com/Yewon-dev/deeplearning-study/blob/main/README.md) 


-----

**컨테이너에 진입**

```bash
docker exec -i [컨테이너 이름 or ID] /bin/bash
```



**Docker 컨테이너 중지**

```bash
docker container [컨테이너 이름 or ID]
```



**Docker 컨테이너 삭제**

```bash
docker rm [컨테이너 이름 or ID] (-f)
```



