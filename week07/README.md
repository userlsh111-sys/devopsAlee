7주차 정리

1. Docker Compose(비유 개념)
  -지휘 시작: docker compose up
  -container라는 연주자들이
  -compose.yaml이라는 악보를 보며
  -services라는 연주파트를 연주한다.

2. DB 관련 주의: 앱과 DB는 다른 container에 넣는다. 앱만 업뎃하려다 DB도 바뀌니..

3. 악보(compose.yaml)
  -반복되는 명령을 yaml 파일에 정의해 여러 container들을 연결시킨다. 
  -REDIS_HOST: 서비스 이름이자 DNS 주소로서, 같은 네트워크가 IP가 바뀌어도 그대로인 DNS 주소를 해석함. 
  -volume: 데이터가 저장되는 곳으로, container가 삭제돼도, 호스트에 있기에 유지됨.
    -docker compose down에 "-v"까지 붙이면 volume도 삭제됨.
  -ports: 안 쓰면 외부엔 노출되지 않지만(내부용), 다른 네트워크로는 접속 안 됨.
  
4. 주의사항
  -.env: yaml 외 파일을 따로 만들어, 환경변수 설정해 비번 가릴 것.
  -요청분배: port(은행입구)를 nginx로 적고(reverse proxy), web에 분산(은행창구 / load balancing)시킨다.
  -healthcheck: yaml 파일의 "depends on" 아래에 "condition: service_healthy"를 입력해 redis(서비스명)가 괜찮은지 먼저 확인함. 




compose ps 결과 
$ docker compose ps
NAME                IMAGE            COMMAND                  SERVICE   CREATED          STATUS          PORTS
guestbook-redis-1   redis:7-alpine   "docker-entrypoint.s…"   redis     49 seconds ago   Up 48 seconds   6379/tcp

down 전후:
$ docker compose down && docker compose up -d
[+] down 3/3
 ✔ Container guestbook-web-1   Removed                                                         3.1s
 ✔ Container guestbook-redis-1 Removed                                                         0.3s
 ✔ Network guestbook_default   Removed                                                         0.2s
[+] up 3/3
 ✔ Network guestbook_default   Created                                                         0.0s
 ✘ Container guestbook-redis-1 Error dependency redis failed to start                          0.8s
 ✔ Container guestbook-web-1   Created                                                         0.1s
dependency failed to start: container guestbook-redis-1 has no healthcheck configured
과정: 해당 글 2개를 쓰고 나서 yaml의 depends_on 부분에 healthy를 추가하고 실행했습니다. 

*scale 생략 후 46p. yaml 코드를 바꿔서 실행이 안 됩니다..
