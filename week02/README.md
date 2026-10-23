2주차 정리
  1. 서버: 
    -bare metal: 1 PC, 1 OS, 여러 소프트웨어
      -OS가 하나라 관리가 쉽지만, 다른 소프트웨어와의 리소스 분담시 수요가 늘면 곤란함.
                                    -하나가 해킹되면 다른 것도 위험하기도.
      -보완: 가상화로써 격리공간에서 실행함.
    -가상화: 서버가 마치 있는 것처럼 만드는 기술(논리적 컴퓨팅)
      -hypervisor: 1 PC, 여러 가상 머신
        -호스트OS로써 게스트OS를 실행함.
          -호스트는 H/W 서버를 관리하며, 게스트는 VM으로서 리소스를 할당 받음.
        -절차: 프로그램, system call, 게스트OS 커널, 가상 H/W, hypervisor, 실제 H/W
      -container: 1 PC, 여러 컨테이너
        -hypervisor보다 빠르며, 호스트와 게스트가 각각 독립적이라 overhead가 큼.
                              -호스트만으로 격리공간(container) 만들 수 있음.
                                          -모든 공간이 호스트의 커널 공유함.
        -리눅스 컨테이너 핵심 기술:
          -namespace: 프로세스, 파일 시스템, 네트워크 등의 공간
          -cgroups(제어 그룹): 리소스 사용량 제어
  2. WSL(Windows Subsystem for Linux)
    -장점: 빠름(VM보다 적은 리소스 사용), 윈도우 파일탐색기로 접근가능, bash 명령어 가능
    -설치:
      -배포(distribution) 목록 확인: wsl --list --online
      -"wsl -l -v"로 설치 여부 확인(verbose: 상세정보)
      -"wsl --install"로 설치(디폴트가 Ubuntu라 Ubuntu로 설치됨.)
    -제거: wsl --unregister (제거할 거)
    -디폴트 실행 설정: wsl --set-default (디폴트 배포판)
  3. 터미널(Ubuntu)
    -디렉터리 생성과 이동: mkdir (디렉터리명), cd (디렉터리명)
    -현 디렉터리 확인: pwd
      -계정(superuser do) 추가: "sudo adduser (이름)" 입력 후 비번도.
      -로그인: "wsl -d (배포판) -u (이름)" 입력 후 비번도.
    -Advanced Package Tool:
      -목록 갱신: sudo apt update
      -업뎃: sudo apt upgrade
      -설치 혹은 제거: 위의 "apt" 다음에 install 혹은 remove (해당 패키지명) 붙일 것.
  4. 기본 리눅스어
    -파일 목록 확인: ls, ls -l, ls -a
                        -long list  -all
      -"-l"로써 사용자와 그룹, 기타 사용자(순) 각자의 read, write, execute 권한을 볼 수 있음.
      -권한 수정(change mode): chmod (권한) (파일명)
        -read 4, write 2, execute 1
    -디렉터리:
      -생성, 삭제: mkdir, rmdir (디렉터리명)
                          -비어있을 때만.
      -cd:
        -~: home
        -..: 상위
        --: 직전
  5. Git어
    -git init: 초기화(git에 올리기 위한 시발점)
      -타 브랜치명으로 올리고 싶다면, "git init -b (브랜치명)"
    -상태(수정됐는지 등) 확인: git status
    -커밋 장전(staging area): git add (해당 파일명)
                              -전부 다: git add .
    -커밋: git commit -m "커밋명"
    -커밋기록 확인: git log
                    -짧게: git log --oneline
  6. GitHub 연결
    -우선 설치: sudo apt install gh
    -로그인: gh auth login 
      -GitHub.com, HTTPS, Yes(인증Authenticate 요망), Login with a web browser, (one-time code 복붙)
    -레포짓(repo) 만들기: gh repo create (레포명) --public --source. --remote=(원격명) --push
                                                  -공개     -원본             -보통 "origin" 씀.
      -확인: gh repo view --web
    -마무리: 커밋, 푸쉬(git push)
