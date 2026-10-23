3주차 정리

1. Qwen: Alibaba Cloud 제작 LLM
  -링크: https://qwen.ai/home
  -실습 모델: 텍스트 처리, 크기 523MB, 출력 512토큰, 입력 최대 300자
2. Ollama: LLM 오픈 소스 플랫폼
  -API: 
    -stream: false(응답 한 번에.)
    -think: false(생각모드 비활성)
3. 실습 구조
  -브라우저(http://localhost:8000): 질문 전송, 답변 표시
  -파이선 웹 앱(chat.py): 질문을 API로 전달함.
  -Ollama 서버(127.0.0.1:11434): 모델 실행
  -qwen3:0.6b
            -Billion(지피티3: 175B)

4. Shell어(pdf 34p. start.sh을 통한 분석)
  -#!(shebang): 이 파일을 (뒤의)프로그램으로 해석해 실행할 것.
    -bash에 따라, #만 있으면 주석이 됨.
  -$: 뒤에 현 스크립트의 이름 혹은 경로 씀. 
                        -공백이 있으면 ""로 둘러쌓을 것.
  -dirname: 디렉터리명만 출력함.
  -$(): 명령어(괄호 안) 실행 후 출력해 넣음(괄호 안).
    -이를테면, pwd와 "$(pwd)"는 같음.
  -||: or 연산
  -exit: 종료
    -성공(True)시 0, 실패(False)시 0 아님.

5. Shell어2(pdf 44p. export.sh를 통한 분석)
  -cat: 입력받으며 그대로 출력하며
  ->: 그 출력을 파일로 보냄.
  -<<: hereDoc 시작
  -EOF: End of File(다른 문자 써도 됨.)
    -따옴표 꼭 단다.(안 달면 변수 잘못됨.)
