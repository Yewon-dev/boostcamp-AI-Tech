# Linux

### 쉘의 종류

- sh : 최초의 쉘
- bash : Linux 표준 쉘
- zsh : Mac 카탈리나 OS 기본 쉘



---

### 기본 명령어

- `man python` : shell command의 메뉴얼 문서 출력
- `mmkdir` : 폴더 생성
- `pwd` : 현재 폴더의 절대경로
- `echo`  : 텍스트 출력
- `sudo` : 관리자 권한으로 실행
- `cp` : 파일 또는 폴더 복사
- `mv` : 파일, 폴더 이동 (이름 바꿀 때 활용)
- `cat` : 특정 파일 내용 출력
- `history` : 최근에 입력한 쉘 커맨드 history 출력
- `find` : 파일 및 폴더 검색
- `export` : 환경변수 설정
- `alias` : 별칭 설정

---

- `sort` : 행단위 정렬

- `uniq` : 중복된 행이 연속으로 있는 경우 중복 제거

  - ``````bash
    cat fruits.txt | sort | uniq | wc -l
    ``````

- `grep` : 파일에 주어진 패턴 목록과 매칭되는 라인 검색
- `cut` : 파일에서 특정 필드 추출

---

**Redirection** : 프로그램의 출력(stdout)을 다른 파일이나 스트림으로 전달

- `>` : 덮어쓰기(overwrite)
- `>>` : 맨 아래에 추가하기(append)

**Pipe** : 프로그램의 출력을 다른 프로그램의 입력으로 사용하고 싶은 경우

- `ls | grep "vi"` : 현재 폴더에 있는 파일명 중 vi가 들어간 단어를 찾음
- `ls | grep "vi" > output.txt` : 그 결과를 output.txt에 저장

----

- `ps` : 현재 실행되고 있는 프로세스 출력

- `curl` : Data transfer 커맨드, Request를 테스트

- `df` : 현재 사용 중인 디스크 용량 확인

- `scp` : SSH을 이용해 네트워크로 연결된 호스트 간 파일을 주고 받음

- `nohup` : 터미널 종료 후에더 계속 작업이 유지되도록 실행(백그라운드 실행)

  - ```bash
    nohup python3 app.py &
    ```

- `chmod` : 파일의 권한 변경

---

### 쉘 스크립트 예시

참고

- https://github.com/zzsza/shell-scripts
- https://github.com/denysdovhan/bash-handbook 
- https://github.com/epety/100-shell-script-examples

