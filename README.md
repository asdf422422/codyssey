# E1-1 |  내 컴퓨터에 개발자용 '작업실' 꾸미기
https://app.notion.com/p/E1-1-3ac1d18148ce80ef954ff694df1c0541
<br> <br>

## 1. 프로젝트 개요
개발자가 자주 쓰는 터미널 및 Docker, 깃허브 설정 방법 알아보기

- 터미널로 디렉토리 및 파일 관리하기 
- Docker 설치 및 기본 운영 명령 습득하기
- Dockerfile 기반 커스텀 이미지 제작
- Git과 GitHub 사용 방법을 익히기

최종적으로 같은 서비스를 여러 번 다른 컴퓨터에서 실행해도 재현되는 사고방식을 익히기
<br> <br>

## 2. 실행 환경
- OS: macOS Sequoia 15.7.4 (Darwin 24.6.0)
- Shell: Zsh(/bin/zsh)
- Terminal: macOS 기본 터미널(Terminal.app)
- Docker: 28.5.2
- Git: 2.53.0
<details>
<summary>확인 방법</summary>

- OS 버전 확인
    
```bash
uname -a
```

실행 결과:

```text
Darwin Kernel Version 24.6.0: Mon Jan 19 22:00: ...
```
<br> <br>
- Docker 버전 확인

```bash
docker --version
```

실행 결과:

```text
Docker version 28.5.2, build ...
```
<br> <br>
- Git 버전 확인

```bash
git --version
```

실행 결과:

```text
git version 2.53.0
```
<br> <br>
- Shell 확인

```bash
echo $SHELL
```

실행 결과:

```text
/bin/zsh
```
</details>
<br>

## 3. 수행 항목 체크리스트
- [ ]  터미널
    - 다음 작업을 터미널로 수행하고, 명령어 + 출력 결과를 기술 문서에 기록한다.
        - 현재 위치 확인, 목록 확인(숨김 파일 포함), 이동, 생성, 복사, 이동/이름변경, 삭제
        - 파일 내용 확인, 빈 파일 생성
- [ ]  권한
    - 권한을 확인/변경하는 명령을 수행하고, 변경 전/후 비교를 기술 문서에 남긴다.
    - 최소 요구: 파일 1개, 디렉토리 1개에 대해 권한 변경 실험을 수행한다.
- [ ]  Docker
    - Docker 버전 확인 결과를 기록한다. (`docker --version`)
    - Docker 데몬 동작 여부 확인 결과를 기록한다. (`docker info` 또는 동등 점검)
    
    - 이미지: 다운로드/목록 확인 (예: `docker images`)
    - 컨테이너: 실행/중지/목록 확인 (예: `docker ps`, `docker ps -a`)
    - 운영: 로그 확인 (예: `docker logs`), 리소스 확인 (예: `docker stats`)
    - 수행 명령과 출력 결과를 기술 문서에 남긴다.
    
    - `hello-world` 실행 성공을 기록한다.
    - `ubuntu` 컨테이너를 실행하고 내부 진입 후 간단 명령(예: `ls`, `echo`) 수행 결과를 기록한다.
    - 컨테이너 종료/유지(attach/exec 등)의 차이를 스스로 관찰하고 간단히 정리한다.
- [ ]  Dockerfile
    - 아래 방식 중 하나를 선택하여 기존 Dockerfile/이미지 기반의 커스텀 이미지를 만든다.
        - (A) 웹 서버 베이스 이미지 활용(예: NGINX/Apache 등) + 정적 콘텐츠/설정만 교체
        - (B) Linux 베이스 이미지(예: ubuntu/alpine 등) + 기본 기능(패키지/사용자/환경변수/헬스체크 등) 추가
    - 제작 결과는 아래 조건을 만족해야 한다.
        - 커스텀 이미지 빌드 성공 및 컨테이너 실행 성공
        - 기술 문서에 다음을 포함한다.
            - 어떤 “기존 베이스(이미지/예시 Dockerfile)”를 선택했는지
            - 내가 적용한 커스텀 포인트 각각의 목적(간단 요약)
            - 빌드/실행 명령 + 핵심 결과(출력/스크린샷)
- [ ]  포트 
    • 브라우저 접속 화면(또는 `curl` 응답)을 기술 문서에 첨부한다.

- [ ]  마운트
- [ ]  볼륨
    - Docker 볼륨을 생성하고 컨테이너에 연결한다.
    - 컨테이너 삭제 전/후로 데이터를 확인하여 데이터가 유지됨을 증명한다.
    - 기술 문서에 생성/연결/검증 절차(명령+출력)를 포함한다.
- [ ]  Git
- [ ]  GitHub
    
    Git 사용자 정보/기본 브랜치 설정을 완료하고
    
    ```
    git config --list
    ```
    
    결과를 기록한다.
    
    - GitHub 로그인 및 저장소 연동을 완료하고, 연동 증거(스크린샷 등)를 기술 문서에 첨부한다.
- [ ]  보안 및 개인정보 보호
    - 기술 문서/로그/스크린샷에 토큰, 비밀번호, 개인키, 인증 코드 등이 포함되지 않도록 마스킹한다.
    - 의심되는 민감정보가 노출된 경우, 즉시 히스토리/문서에서 제거하고 재발급 절차를 수행한다 (가능한 범위에서).
     
<br><br>
## 4. 검증 방법
<details> <summary>4-1. 터미널 조작 로그 기록 </summary>
    
- A. 현재 위치 확인
```bash
pwd
```

실행 결과:

```text
/Users/(사용자)
```
<br> <br>
- B. 목록 확인(숨김 파일 포함)
```bash
ls -a
```

실행 결과:

```text
.			.vscode			Library
..			.zsh_history		Movies
.CFUserTextEncoding	.zsh_sessions		Music
.docker			Applications		OrbStack
.DS_Store		codysseyEP1-1		Pictures
.orbstack		Desktop			Public
.ssh			Documents
.Trash			Downloads
```
<br> <br>
- C. 이동
```bash
(사용자) ~ % cd codysseyEP1-1
```

실행 결과:

```text
(사용자) codysseyEP1-1 % 
```
<br> <br>
- D. 생성
```bash
mkdir test
```

실행 결과:

```text
(사용자) codysseyEP1-1 % ls
test
```
<br> <br>
- E. 복사
```bash
cp -r test testcopy
```

실행 결과:

```text
(사용자) codysseyEP1-1 % ls
test		testcopy
```
<br> <br>
- F. 이동/이름 변경
이동
```bash
mv test.txt test
```

실행 결과:

```text
(사용자) test % ls
test.txt
```

이름 변경
```bash
mv test.txt test2.txt
```

실행 결과:

```text
(사용자) test % ls
test		test2.txt	testcopy
```
<br> <br>
- G. 삭제
```bash
rm -r testcopy
```

실행 결과:

```text
(사용자) codysseyEP1-1 % ls
test
```
<br> <br>
- H. 파일 내용 확인
```bash
cat test.txt
```

실행 결과:

```text
hi
hello world
3rd row
```
<br> <br>
- I. 빈 파일 생성
```bash
touch test.txt
```

실행 결과:

```text
(사용자) codysseyEP1-1 % ls
test		test.txt
```
<br> <br>
- J. 권한
권한 확인
```bash
ls -l
```

실행 결과:

```text
total 8
drwxr-xr-x  3 (사용자)  (사용자)  96  7 30 20:53 test
-rw-r--r--  1 (사용자)  (사용자)  23  7 30 21:09 test.txt
```
권한 변경
```bash
chmod 755 test.txt
chmod o-r test
```

실행 결과:

```text
total 8
drwxr-x--x  3 (사용자)  (사용자)  96  7 30 20:53 test
-rwxr-xr-x  1 (사용자)  (사용자)  23  7 30 21:09 test.txt
```
</details>

<details> <summary>4-2. Docker </summary>

- 0. Docker란 무엇인가?

https://app.notion.com/p/Docker-3ad1d18148ce8070afc6f4b75f60174f
<br> <br>
- A. 버전 확인
```bash
docker --version
```

실행 결과:

```text
Docker version 28.5.2, build ecc6942
```
<br> <br>
- B. 동작 여부 확인
```bash
docker info
```

<details> <summary>실행 결과 </summary>

```text
Client:
 Version:    28.5.2
 Context:    orbstack
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.29.1
    Path:     /Users/(사용자)/.docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.40.3
    Path:     /Users/(사용자)/.docker/cli-plugins/docker-compose

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 28.5.2
 Storage Driver: overlay2
  Backing Filesystem: btrfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Swarm: inactive
 Runtimes: runc io.containerd.runc.v2
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 1c4457e00facac03ce1d75f7b6777a7a851e5c41
 runc version: d842d7719497cc3b774fd71620278ac9e17710e0
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.17.8-orbstack-00308-g8f9c941121b1
 Operating System: OrbStack
 OSType: linux
 Architecture: x86_64
 CPUs: 12
 Total Memory: 15.67GiB
 Name: orbstack
 ID: (ID)
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  ::1/128
  127.0.0.0/8
 Live Restore Enabled: false
 Product License: Community Engine
 Default Address Pools:
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: (IP), Size: 24
   Base: fd07:b51a:cc66:d000::/56, Size: 64

WARNING: DOCKER_INSECURE_NO_IPTABLES_RAW is set
```

</details>



<br> <br>

- C. 이미지 <br>
이미지 목록 확인
```bash
docker images
```

실행 결과:

```text
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```
이미지 다운로드 
```bash
docker pull ubuntu
```

실행 결과:

```text
Using default tag: latest
latest: Pulling from library/ubuntu
ed819469700f: Pull complete 
a3679419df18: Pull complete 
Digest: sha256:3131b4cc82a783df6c9df078f86e01819a13594b865c2cad47bd1bca2b7063bb
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```
<br> <br>
- D. 컨테이너
실행
```bash
docker run -d --name mynginx -p 8080:80 nginx
```

실행 결과:

```text
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
062e450697fa: Pull complete 
82454cdbf456: Pull complete 
3c7ab7949321: Pull complete 
cacfcdd01f30: Pull complete 
b6698f04e005: Pull complete 
2bedaf25031a: Pull complete 
d26f27cc8c41: Pull complete 
Digest: sha256:5a88c9c45479443d7be2eadc894b4ed0a9801bae03d97a5760ae13b5c2005942
Status: Downloaded newer image for nginx:latest
682e3d59fee0fa0dc84b1215c95555fde07191f82aaf09517686ad005cf1f238
```
정지
```bash
docker stop mynginx
```

실행 결과:

```text
mynginx
```
목록 보기
```bash
docker ps -a
```

실행 결과:

```text
CONTAINER ID   IMAGE         COMMAND                   CREATED          STATUS                      PORTS                                     NAMES
682e3d59fee0   nginx         "/docker-entrypoint.…"   7 minutes ago    Up 7 minutes                0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   mynginx
c43e5d77166a   hello-world   "/hello"                  9 minutes ago    Exited (0) 9 minutes ago                                              elegant_lamarr
dfe9a6265ec6   ubuntu        "bash"                    13 minutes ago   Exited (0) 9 minutes ago                                              myubuntu
17f185ec2941   ubuntu        "/bin/bash"               27 minutes ago   Exited (0) 26 minutes ago                                             kind_chaplygin

```
<br> <br>


- E. 운영/리소스
운영 로그 확인
```bash
docker logs mynginx
```



<details> <summary>실행 결과:</summary>

```text
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/07/31 03:17:52 [notice] 1#1: using the "epoll" event method
2026/07/31 03:17:52 [notice] 1#1: nginx/1.31.3
2026/07/31 03:17:52 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19) 
2026/07/31 03:17:52 [notice] 1#1: OS: Linux 6.17.8-orbstack-00308-g8f9c941121b1
2026/07/31 03:17:52 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 20480:1048576
2026/07/31 03:17:52 [notice] 1#1: start worker processes
2026/07/31 03:17:52 [notice] 1#1: start worker process 29
2026/07/31 03:17:52 [notice] 1#1: start worker process 30
2026/07/31 03:17:52 [notice] 1#1: start worker process 31
2026/07/31 03:17:52 [notice] 1#1: start worker process 32
2026/07/31 03:17:52 [notice] 1#1: start worker process 33
2026/07/31 03:17:52 [notice] 1#1: start worker process 34
2026/07/31 03:17:52 [notice] 1#1: start worker process 35
2026/07/31 03:17:52 [notice] 1#1: start worker process 36
2026/07/31 03:17:52 [notice] 1#1: start worker process 37
2026/07/31 03:17:52 [notice] 1#1: start worker process 38
2026/07/31 03:17:52 [notice] 1#1: start worker process 39
2026/07/31 03:17:52 [notice] 1#1: start worker process 40
192.168.215.1 - - [31/Jul/2026:03:19:11 +0000] "GET / HTTP/1.1" 200 896 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/146.0.0.0 Safari/537.36" "-"
2026/07/31 03:19:11 [error] 30#30: *1 open() "/usr/share/nginx/html/favicon.ico" failed (2: No such file or directory), client: 192.168.215.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost:8080", referrer: "http://localhost:8080/"
192.168.215.1 - - [31/Jul/2026:03:19:11 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://localhost:8080/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/146.0.0.0 Safari/537.36" "-"
2026/07/31 03:31:57 [notice] 1#1: signal 3 (SIGQUIT) received, shutting down
2026/07/31 03:31:57 [notice] 31#31: gracefully shutting down
2026/07/31 03:31:57 [notice] 32#32: gracefully shutting down
2026/07/31 03:31:57 [notice] 37#37: gracefully shutting down
2026/07/31 03:31:57 [notice] 35#35: gracefully shutting down
2026/07/31 03:31:57 [notice] 31#31: exiting
2026/07/31 03:31:57 [notice] 32#32: exiting
2026/07/31 03:31:57 [notice] 38#38: gracefully shutting down
2026/07/31 03:31:57 [notice] 37#37: exiting
2026/07/31 03:31:57 [notice] 35#35: exiting
2026/07/31 03:31:57 [notice] 39#39: gracefully shutting down
2026/07/31 03:31:57 [notice] 38#38: exiting
2026/07/31 03:31:57 [notice] 30#30: gracefully shutting down
2026/07/31 03:31:57 [notice] 39#39: exiting
2026/07/31 03:31:57 [notice] 30#30: exiting
2026/07/31 03:31:57 [notice] 35#35: exit
2026/07/31 03:31:57 [notice] 31#31: exit
2026/07/31 03:31:57 [notice] 37#37: exit
2026/07/31 03:31:57 [notice] 32#32: exit
2026/07/31 03:31:57 [notice] 38#38: exit
2026/07/31 03:31:57 [notice] 39#39: exit
2026/07/31 03:31:57 [notice] 40#40: gracefully shutting down
2026/07/31 03:31:57 [notice] 30#30: exit
2026/07/31 03:31:57 [notice] 34#34: gracefully shutting down
2026/07/31 03:31:57 [notice] 40#40: exiting
2026/07/31 03:31:57 [notice] 34#34: exiting
2026/07/31 03:31:57 [notice] 33#33: gracefully shutting down
2026/07/31 03:31:57 [notice] 36#36: gracefully shutting down
2026/07/31 03:31:57 [notice] 33#33: exiting
2026/07/31 03:31:57 [notice] 29#29: gracefully shutting down
2026/07/31 03:31:57 [notice] 36#36: exiting
2026/07/31 03:31:57 [notice] 29#29: exiting
2026/07/31 03:31:57 [notice] 40#40: exit
2026/07/31 03:31:57 [notice] 36#36: exit
2026/07/31 03:31:57 [notice] 34#34: exit
2026/07/31 03:31:57 [notice] 33#33: exit
2026/07/31 03:31:57 [notice] 29#29: exit
2026/07/31 03:31:57 [notice] 1#1: signal 17 (SIGCHLD) received from 29
2026/07/31 03:31:57 [notice] 1#1: worker process 29 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: signal 29 (SIGIO) received
2026/07/31 03:31:57 [notice] 1#1: signal 17 (SIGCHLD) received from 31
2026/07/31 03:31:57 [notice] 1#1: worker process 31 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: signal 29 (SIGIO) received
2026/07/31 03:31:57 [notice] 1#1: signal 17 (SIGCHLD) received from 33
2026/07/31 03:31:57 [notice] 1#1: worker process 30 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: worker process 33 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: signal 29 (SIGIO) received
2026/07/31 03:31:57 [notice] 1#1: signal 17 (SIGCHLD) received from 38
2026/07/31 03:31:57 [notice] 1#1: worker process 38 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: worker process 40 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: signal 29 (SIGIO) received
2026/07/31 03:31:57 [notice] 1#1: signal 17 (SIGCHLD) received from 40
2026/07/31 03:31:57 [notice] 1#1: signal 17 (SIGCHLD) received from 34
2026/07/31 03:31:57 [notice] 1#1: worker process 34 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: worker process 39 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: signal 29 (SIGIO) received
2026/07/31 03:31:57 [notice] 1#1: signal 17 (SIGCHLD) received from 37
2026/07/31 03:31:57 [notice] 1#1: worker process 35 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: worker process 36 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: worker process 37 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: signal 17 (SIGCHLD) received from 36
2026/07/31 03:31:57 [notice] 1#1: worker process 32 exited with code 0
2026/07/31 03:31:57 [notice] 1#1: exit

```

</details>
<br> <br>
리소스 확인
```bash
docker stats mynginx
```

실행 결과:

```text
682e3d59fee0   mynginx   0.00%     25.2MiB / 15.67GiB   0.16%     1.13kB / 126B   16.2MB / 0B   13 
```
<br> <br>


- F. hello-world 실행
```bash
docker run hello-world
```

실행 결과:

```text
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
Digest: sha256:c3cbe1cc1aa588a64951ac6286e0df7b27fe2e6324b1001c619bb358770c0178
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```
<br> <br>
- G. ubuntu 컨테이너
ubuntu 실행
```bash
docker run -it --name myubuntu ubuntu bash
```

실행 결과:

```text
root@dfe9a6265ec6:/# 
```
ls
```bash
ls
```

실행 결과:

```text
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
```
echo
```bash
echo "Hello Ubuntu"
```

실행 결과:

```text
Hello Ubuntu
```
<br> <br>
- H. 컨테이너 종료/유지

#### 컨테이너 종료

- 컨테이너의 *주 프로세스(PID 1)가 끝난 상태*
- 컨테이너 자체는 남아 있을 수 있지만 실행은 멈춤
- CPU, 메모리를 사용하지 않음
- 다시 시작할 수 있음

#### 컨테이너 유지 (Running)

- 컨테이너의 *주 프로세스가 계속 실행 중인 상태*
- 서비스 제공 가능
- 로그 확인, 접속, 요청 처리 가능```bash


</details>




<details> <summary>4-3. Dockerfile </summary>


(A) 웹 서버 베이스 이미지 활용(예: NGINX/Apache 등) + 정적 콘텐츠/설정만 교체

1. 어떤 “기존 베이스(이미지/예시 Dockerfile)”를 선택했는지
: **nginx**

2. 내가 적용한 커스텀 포인트 각각의 목적(간단 요약)
: **쉽게 적용될 수 있도록 간단한 내용으로 바꿈**

3. 빌드/실행 명령 + 핵심 결과(출력/스크린샷)
<details> <summary>빌드 명령 </summary>

```bash
touch Dockerfile index.html
nano Dockerfile
nano index.html
```

Dockerfile 수정 
```bash
FROM nginx:la›test
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80 #포트
```

index.html 수정 
```bash
<!DOCTYPE html>
<html>
<head>
<title>Hello Docker</title>
</head>
<body>
<h1>Hello Docker!</h1>
</body>
</html>
```

빌드
```bash
docker build -t my-web .
```

실행 결과:

```text
[+] Building 8.0s (7/7) FINISHED                                docker:orbstack
 => [internal] load build definition from Dockerfile                       0.2s
 => => transferring dockerfile: 116B                                       0.0s
 => [internal] load metadata for docker.io/library/nginx:latest            2.4s
 => [internal] load .dockerignore                                          0.1s
 => => transferring context: 2B                                            0.0s
 => [1/2] FROM docker.io/library/nginx:latest@sha256:5a88c9c45479443d7be2  4.3s
 => => resolve docker.io/library/nginx:latest@sha256:5a88c9c45479443d7be2  0.2s
 => => sha256:4e5db4761e0ff445f7fd29aad680ad28e8abf7d2048 9.09kB / 9.09kB  0.0s
 => => sha256:062e450697faa5f02a3a74eba9864ee4d79bc9cfb 29.78MB / 29.78MB  0.7s
 => => sha256:5a88c9c45479443d7be2eadc894b4ed0a9801bae0 10.23kB / 10.23kB  0.0s
 => => sha256:db4f612f385437d11eb26620a4f1d7efb3ff44e1296 2.29kB / 2.29kB  0.0s
 => => sha256:3c7ab7949321f47c96fc0918f9f72e8f51bd452cdef1e0d 626B / 626B  0.7s
 => => sha256:82454cdbf456a77f9ff1bb88b121c2a739e38c30e 33.33MB / 33.33MB  1.0s
 => => extracting sha256:062e450697faa5f02a3a74eba9864ee4d79bc9cfbd65769f  1.1s
 => => sha256:cacfcdd01f309c65d69372716e799ea741065ac1b1e6088 955B / 955B  1.0s
 => => sha256:b6698f04e005497a7f495c0719358d43890cb3997ad7b4a 403B / 403B  1.1s
 => => sha256:2bedaf25031a24fb70b9dc2d56cb17139186d1ae5fd 1.21kB / 1.21kB  1.2s
 => => sha256:d26f27cc8c41e321394cb3c9a80915d90d5f1f1d3cb 1.40kB / 1.40kB  1.3s
 => => extracting sha256:82454cdbf456a77f9ff1bb88b121c2a739e38c30ea689c13  0.7s
 => => extracting sha256:3c7ab7949321f47c96fc0918f9f72e8f51bd452cdef1e0da  0.0s
 => => extracting sha256:cacfcdd01f309c65d69372716e799ea741065ac1b1e60880  0.0s
 => => extracting sha256:b6698f04e005497a7f495c0719358d43890cb3997ad7b4ab  0.0s
 => => extracting sha256:2bedaf25031a24fb70b9dc2d56cb17139186d1ae5fd2054e  0.0s
 => => extracting sha256:d26f27cc8c41e321394cb3c9a80915d90d5f1f1d3cbbbcda  0.0s
 => [internal] load build context                                          0.2s
 => => transferring context: 157B                                          0.0s
 => [2/2] COPY index.html /usr/share/nginx/html/index.html                 0.4s
 => exporting to image                                                     0.3s
 => => exporting layers                                                    0.2s
 => => writing image sha256:034b906152eb442a0453f93ba92d8cdec5d158b374ce0  0.0s
 => => naming to docker.io/library/my-web                                  0.0s
```

</details>

<details> <summary>실행 명령 </summary>
    
```bash
docker run -p 8080:80 my-web
```

실행 결과:

```text
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/07/31 04:56:15 [notice] 1#1: using the "epoll" event method
2026/07/31 04:56:15 [notice] 1#1: nginx/1.31.3
2026/07/31 04:56:15 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19) 
2026/07/31 04:56:15 [notice] 1#1: OS: Linux 6.17.8-orbstack-00308-g8f9c941121b1
2026/07/31 04:56:15 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 20480:1048576
2026/07/31 04:56:15 [notice] 1#1: start worker processes
2026/07/31 04:56:15 [notice] 1#1: start worker process 29
2026/07/31 04:56:15 [notice] 1#1: start worker process 30
2026/07/31 04:56:15 [notice] 1#1: start worker process 31
2026/07/31 04:56:15 [notice] 1#1: start worker process 32
2026/07/31 04:56:15 [notice] 1#1: start worker process 33
2026/07/31 04:56:15 [notice] 1#1: start worker process 34
(IP) - - [31/Jul/2026:04:57:57 +0000] "GET / HTTP/1.1" 200 120 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/146.0.0.0 Safari/537.36" "-"
(IP) - - [31/Jul/2026:04:57:57 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://localhost:8080/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/146.0.0.0 Safari/537.36" "-"
2026/07/31 04:57:57 [error] 29#29: *1 open() "/usr/share/nginx/html/favicon.ico" failed (2: No such file or directory), client: 192.168.215.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost:8080", referrer: "http://localhost:8080/"
2026/07/31 04:58:32 [notice] 1#1: signal 28 (SIGWINCH) received
2026/07/31 04:58:32 [notice] 1#1: signal 28 (SIGWINCH) received

```
</details>

접속 증거: https://app.notion.com/p/Dockerfile-3ad1d18148ce80afa160c49f8f97c84a?source=copy_link#3ae1d18148ce80a8a04ad0fc3b3341c6
<br> <br>

</details>


<details> <summary>4-4. 마운트/볼륨 </summary>

**1. 마운트 바인드**
A. 컨테이너 실행 전 파일 생성
```bash
mkdir persistTest
cd persistTest
echo “host file before container” > test.txt
```
B. 컨테이너 생성
```bash 
docker run -it --name bind-test -v /Users/(사용자)/codysseyEP1-1/codyssey/persistTest:/data ubuntu bash
```
C. 컨테이너 내부 파일 수정
```bash 
echo "changed inside container" > /data/test.txt
```
D. 컨테이너 제거
```bash 
docker rm bind-test
```
E. 파일 확인 
```bash
cat test.txt
```
실행 결과: 
```
changed inside container
```
<br> <br>

**2. 볼륨**
A. 볼륨 생성
```bash
docker volume create ubuntu-data
```

B. 컨테이너 생성 및 볼륨에 연결
```bash
docker run -it --name volume-test -v ubuntu-data:/data ubuntu bash
```
C. 컨테이너 내부 파일 생성
```bash
echo "volume persistent data" > /data/test.txt
cat /data/test.txt
```
D. 컨테이너 삭제
```bash
docker rm volume-test
```
E. 새 컨테이너 생성 후 데이터 확인
```bash
docker run -it --name volume-test-new -v ubuntu-data:/data ubuntu bash
cat /data/test.txt
```

실행 결과:

```text
volume persistent data
```
</details>

<details> <summary>4-5. Git/GitHub </summary>
```bash

```

실행 결과:

```text

```
<br> <br>
    
</details>


## 5. 트러블슈팅
### 5-1.
### 5-2.
