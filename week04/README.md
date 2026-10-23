4주차 정리

1. 파일 찾기
  -shell 스크립트 파일: find . -type f -name "*.sh"
                                                   -형식이 sh니까.
  -특정 내용("exit 1")이 들어가는 파일: grep -R -n "exit 1" week03 2>/dev/null
                                            -R: 하위 디렉토리까지.
                                                -n: 줄 번호 표시
    -파일수 보려면... "| wc -l" 추가할 것.
                        -word count
  -|(파이프라인): 앞 명령 출력을 뒤 명령의 입력으로 이음.
  -grep(Global, Regular Expression, Print): 텍스트에서 원하는 줄을 검색하는 명령

2. 파일 검사(조건문)
  --z: 문자열 길이 0이냐?
  --n: 문자열 길이 0 아니지?
  --eq: 같은 정수냐?
  --ne: 다른 정수지? 
  --gt: 더 큰 정수냐?
  --ge: 이상
  --lt: 더 작은 정수지?
  --le: 이하

3. 프로세스
  -프로그램(저장된 실행 코드) vs. 프로세스(실행 중인 프로그램)
  -ps aux: 실행 중인 프로세스 보여줌.
  -tar: 여러 파일, 하나의 아카이브(z: gzip / f: ㅏ일명 뒤에 쓰기)
    --tzf: 목록확인
    --xzf: eXtract(압축해제)
    --czf: 압축생성
    --C: cd
  -diff
    --rq: recursive brief("A and B differ"처럼 간단히 보여줌.)

4. 협업
  -브랜치 생성: git switch -c (새 브랜치명)
  -현 브랜치 확인: git branch 
  -이어쓰기: "cat >>"(">" 2개) 
  -Pull Request: gh pr 
  -Merge: gh pr merge --squash --delete-branch
    -현 브랜치가 main과 merge됨. 
    -같은 커밋에서 다르게 수정되면 Conflict돼 실패함.
      -해당 파일에서 두 후보(파일)들 중 원하는 하나를 남기고 나머지 하나를 싹다 지워 수정함.
      -add, commit, push 후 깃헙에 들어가(gh pr view --web) merge 버튼을 누른다.

5. 네트워크(기본개념)
  -IP: 네트워크에서 장치(내 컴 등)를 식별시키는 주소
    -ip addr: wsl에서 본 명령어로 볼 수 있음.
  -port: 내 컴 안의 서비스(크롬, MySQL 등)를 식별시키는 주소
  -Domain Name System: 도메인(링크 등)을 IP로 변환하는 역할
    -"dig (도메인명)": Domain Information Groper(도메인의 IP 등 정보 조회 / 'dnsutils' install 요망)
  -ping: 응답(연결 여부) 확인
6. 서버 통신
  -curl: html 본문 확인(I는 헤더만, s는 값을 가져오고, o는 파일로 저장함.)
  -ss -tlnp: Tcp, Listen(대기), Num, Process
    -사용 중인 포트 접근시 충돌해서 대기 여부를 확인해야.
    -뒤에 "| grep (포트번호)"를 붙여 해당 포트를 볼 수도.
