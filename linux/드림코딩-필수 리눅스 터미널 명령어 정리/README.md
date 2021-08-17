## 필수 리눅스 터미널 명령어 정리 | 배쉬, 파워쉘 (Bash, PowerShell) 튜토리얼! 가좌아
- https://www.youtube.com/watch?v=EL6AQl-e3AQ

### 명령어 정리
- man, clear, pwd, ls, ls -l, ls -al, open, cd, cat, mkdir, ..
- `cd -` 이전 경로로 이동
- `find . -type file -name "*.txt"` 현재 경로에서 file 타입의 이름이 .txt로 끝나는 파일 검색
- `find . -type directory -name "*.txt"` 현재 경로에서 file 타입의 이름이 .txt로 끝나는 디렉토리 검색
- `which node` node 명령어의 실제 경로
- `touch new_file.txt` 파일생성
- `echo "hello world"` hello world 문자열 출력
- `echo "hello world" > new_file3.txt` 해당 파일에 echo 명령어 문자열을 덮어씌운다. (파일이 없으면 생성됨)
- `echo "hello world" >> new_file3.txt` 해당 파일에 echo 명령어 문자열을 이어붙인다. apppend (파일이 없으면 생성됨)
- `mkdir -p dir1/dir2/new_file.txt` 디렉토리까지 한번에 만드는 옵션
- `cp file.txt dir1/` 복사 
- `rm -r dir2` -r 옵션은 recursive의 약자다. (재귀적으로 내부 디렉토리도 삭제)

---
- grep (Global regular expression print) 키워드로 검색하기
- `grep "world" *.txt` \*.txt 파일에서 world 키워드 찾기
- `grep -n "world" *.txt` -n 옵션으로 몇번째 줄에 있는지 표기함
- `grep -i "world" *.txt` -i 옵션으로 대소문자 구분을 없앰 (ignore)

---
- 환경변수 관련
- `export MY_DIR="dir1"` 환경변수 설정
- `env` 설정되어있는 환경변수 확인
- `cd $MY_DIR` $를 이용하여서 환경변수를 사용
- `unset MY_DIR` 환경변수 삭제
