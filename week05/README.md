HTTP/1.1 200 OK
Server: nginx/1.31.6
Date: Tue, 06 Oct 2026 17:48:29 GMT
Content-Type: text/html
Content-Length: 27
Last-Modified: Wed, 30 Sep 2026 03:30:57 GMT
Connection: keep-alive
ETag: "6abc8271-1b"
Accept-Ranges: bytes

HTTP/1.1 200 OK
Server: nginx/1.31.6
Date: Tue, 06 Oct 2026 17:48:37 GMT
Content-Type: text/html
Content-Length: 27
Last-Modified: Wed, 30 Sep 2026 03:32:33 GMT
Connection: keep-alive
ETag: "6abc82d1-1b"
Accept-Ranges: bytes

HTTP/1.1 200 OK
Server: nginx/1.31.6
Date: Tue, 06 Oct 2026 17:48:42 GMT
Content-Type: text/html
Content-Length: 29
Last-Modified: Wed, 30 Sep 2026 03:33:11 GMT
Connection: keep-alive
ETag: "6abc82f7-1d"
Accept-Ranges: bytes




5주차 정리

1. Docker(개발, 배포, 실행을 위한 오픈 플랫폼)
  -애플리케이션과 실행환경을 Container로 묶어, 서로 다른 환경에서도 동일하게 실행토록 함.
  -특장점: 하나의 OS 커널을 공유하는 컨테이너라 VM보다 비교적 가벼우며 말 그대로 격리돼있음.
  -요소
    -image: 읽기 전용 템플릿(틀, 클래스)
    -container: 이미지로부터 생성된 인스턴스(반죽, 객체)
    -dockerfile: 이미지 레시피
    -registry: 이미지 저장 및 공유 장소
  -설치: 크롬에서 검색 후 설치, 터미널로 실행 전에도 먼저 응용 프로그램을 킬 것.

2. Docker Container
  -docker run -d -p 8080:80 --name web nginx: 
           -d(백그라운드 실행)         -이미지 name(여기선 "nginx")
                            -컨테이너 name(여기선 "web")
                 -포트: 호스트(8080)->컨테이너(80)
  -container는 다 격리돼있어 같아도 되지만, 호스트는 달라야 함.
  -환경변수 주입: 포트 다음에 "-e (환경변수=변수명)"을 씀. 

3. Docker 명령어
  -ps: 실행 중인 container("-a" 붙이면 멈춘 것까지.)
  -logs web: 현재까지의 container 로그
    -"-f" 붙이면 실시간으로 계속 봄.
  -stop (container명): 정지, ps에서 안 보임. 
    -restart나 start로 다시 시작할 수 있음.
  -rm (container명): 삭제
    -"-f" 붙이면 실행 중이어도 삭제함.
