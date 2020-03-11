# Opertaions

## 리눅스 (20.03.03~)
### 유닉스의 탄생과 운영체제의 의미
> 운영체제(Operating System)은 시스템 하드웨어를 관리할 뿐 아니라 응용 소프트웨어를 실행하기 위하여 하드웨어 추상화 플랫폼과 공통 시스템 서비스를 제공하는 시스템 소프트웨어이다.
- 운영체제가 없다면 각각의 소프트웨어는 하드웨어를 조작하기 위한 저수준의 작업들을 모두 신경써야 할 것이다.
- UNIX는 이러한 아이디어에서 출발했다. UNIX를 조작하기 위한 언어가 C언어다.
- 여러 UNIX 버전들이 나오게 되었고, 운영체제 인터페이스를 표준화하기 시작했다. =POSIX(Portable Operation System Interface)
- 유료UNIX에 반발하여 GNU라는 단체에서 무료 UNIX 프로젝트가 시작되었다.
- 리눅스는 무료 오픈소스 UNIX다.

### 오픈소스 라이센스
- 대표적인 오픈소스 라이센스
	1. Apache License 2.0 : 아파치 라이선스 2.0이 적용된 오픈소스를 이용하여 개발 하였다면 소스코드를 공개할 필요는 없지만, 아파치 라이선스에 의해 개발되었음을 표시해야 한다.
	2. GNU General Public License (GPL) : GPL이 적용된 오픈소스를 이용하여 개발 하였다면 개발된 소스코드 역시 공개해야 한다. 
	3. MIT License : 사실상 라이센스가 없다. 반드시 오픈소스로 배포해야 한다는 규정이 없고, 라이센스 명시나  소스코드 공개도 하지 않아도 된다.

### 셸(Shell)과 프롬프트
> 셸은 운영 체제 상에서 다양한 운영 체제 기능과 서비스를 구현하는 인터페이스를 제공하는 프로그램이다. 셸(껍데기의 영어 단어)은 사용자와 운영 체제의 내부(커널) 사이의 인터페이스를 감싸는 층이기 때문에 그러한 이름이 붙었다.

- 셸은 일반적으로 명령 줄과 그래픽 형의 두 종류로 분류된다. 명령 줄 셸은 운영 체제 상에서 명령 줄 인터페이스(CLI)를 제공하는 반면에, 그래픽 셸은 그래픽 사용자 인터페이스(GUI)를 제공한다.
	- 그래픽 셸은 대표적으로 윈도 탐색기, 맥의 파인더가 있다.
	- 명령 줄 셸은 대표적은 유닉스 본 셸(bash), 윈도의 cmd가 있다.

- 프롬프트(prompt)는 컴퓨터 터미널의 CLI(커맨드 라인 인터페이스)의 명령줄 대기모드를 가리킨다.
	- $(dollar sign)은 일반유저를 말한다.
	- #(pound sign 혹은 hash mark)는 root권한을 가진 유저 (혹은 어드민, 관리자)를 말한다.

- sudo : 일반유저가 슈퍼유저(super user do) 권한이 필요한 경우 사용한다.
	- $sudo reboot (root 권한 실행)
	- $sudo su - root (root권한 유저로 전환 switch user)

### 리눅스 파일 시스템 구조
- 리눅스 디렉토리 구조는 다음 링크 참고 https://webdir.tistory.com/101?category=561456

### 리눅스 셸 다루기
- 탭하면 자동완성
- 위아래 하면 앞서서 사용했던 명령어
- man, --help 도움말
- 확장자를 생략하는 경우가 있다.

### 파일 경로와 순회
- pwd : 현재 디렉토리 경로를 출력
- ls : 파일 목록 나열
	- ls -l
	- ls workspace/ (workspace 파일 목록)
	- ls *.java (.java 확장자를 갖는 파일들의 목록)

- cd : 디렉토리 변경
	- cd var
	- cd /usr/mygame
	- cd ../../

- ~ 표시는 홈디렉토리를 뜻한다.
- **man : 명령어의 매뉴얼을 출력**
	- man ls
	- ls --help (man말고 --help 옵션으로도 확인가능)

### 파일 관리 명령어
- mkdir : 디렉토리 생성
- rmdir : 디렉토리 삭제
- touch : 빈 파일 생성
	- touch text.txt
- mv : 파일 이동 / 변경 (파일명 바꾸기)
	- mv test.txt workspace/ (test.txt 파일을 workspace 디렉토리 아래로 이동)
- rm : 파일 삭제
	- rm -r workspace/ (해당 디렉토리와 하위 디렉토리들을 재귀적으로(recursive)하게 모두 삭제)
	- rm -ri workspace/ (하위 디렉토리들을 하나씩 확인하는 과정으로 상호작용(interaction) 하면서 지운다.)
- cp : 파일(디렉토리) 복사
	- cp text.txt test.cpy

### 파일 찾기와 파일 정보 확인하기
- find : 파일 검색
	- find . -name Hello.java (현재 디렉토리에서 Hello.java라는 이름의 파일을 검색)
	- find . -name *.java (현재 디렉토리에서 .java로 끝나는 이름의 파일을 검색)
	- find . -size +1 (현재 디렉토리에서 size가 1 이상인 파일 검색, 기본 단위는 512kb)
	- find . -size +1c (현재 디렉토리에서 size가 1byte 이사인 파일 검색)
	- find . -name *.java -size +1c (옵션의 조합도 가능)

- cat, head, tail : 파일 내용 출력하기
	- cat Hello.java (모두 출력)
	- head -n2 Hello.java (맨 앞 2줄만 출력)
	- tail -n2 Hello.java (맨 뒤 2줄만 출력)

- grep : 파일 내부의 내용 검색하기
	- grep "class" Hello.java (Hello.java 파일 내부에서 "class"라는 
단어 검색)
	- grep -i "Hello" Hello.java (대소문자를 무시(ignore)하고 모두 
검색하기)

- cmp : 두개의 파일 정보(줄수, 용량) 비교하기 (compare)
	- cmp Hello.java Hello1.java

- diff : 두개의 파일의 다른 내용 비교해서 보기
	- diff Hello.java Hello1.java

- file : 파일의 정보 확인하기
	- file Hello.java
	- cf) 리눅스에서는 . 뒤에 붙는 확장자를 생략하는 경우가 
종종있다.   

### 유용한 명령어
- clear : 화면 지우기
- history : 입력한 명령어들을 쭉 보여줌
	- !96 (history의 96번 명령어를 다시 실행)
- echo : 화면에 출력
	- echo "hello"
- \> (redirection) : 이전 명령어의 결과를 파일 혹은 스트림의 입력으로 사용한다.
	- echo "Hello" > test (Hello 출력을 test라는 파일에 덮어 쓴다.)
	- echo "Hello" >> test (이어서 쓴다.)

- | (piping) : 이전 명령어의 결과를 다음 명령어의 입력으로 사용한다.
	- cat test | grep He (test 파일의 출력에서 He를 찾는다.)
	- ls -l | less (목록이 많은 경우 일부만 본다.)
	- ls | more

- ; (sequence) : 여러 명령어들을 한줄에 이어서 쓰고 싶은 경우
	- touch test1; echo "okay~" >> test1; cat test1  	

### 파일 압축 관리 (tar)
- tar(Tape ARchive) 묶음, zip 압축
- 압축하기
	- tar -cf name.tar a b c (a,b,c 파일을 name.tar로 묶음)
	- tar -cf name.tar * (현재 디렉토리 파일들 모두 묶음)
	- tar -zcf name.tar.gz a b c (+ 묶고 압축까지)
- 압축풀기
	- tar -xvf name.tar
	- tar -zxvf name.tar.gz

- -f : 파일 이름을 지정
- -c : 파일을 tar로 묶음
- -x : tar 압출을 풂
- -v : 작업 내용을 자세히 출력
- -z : gzip으로 압축하거나 해제함
- -t : 목록 출력
- -p : 파일 권한을 저장
- -C : 경로를 지정

### JDK 설치하기
- wget : 다운로드 
	- wget http://....
- tar -zxvf jdk-8u161-linux-x64.tar.gz (압출풀기)
- (압축푼 디렉토리에서) ./java -version : 버전 확인  

### 링크파일 사용하기
- ls -l 출력시에 맨 앞이 d 이면 디렉토리, - 이면 파일, l 이면 링크파일이다.
링크파일은 윈도우의 바로가기와 비슷한 개념이다.
- 링크파일은 Symbolic Link 와 Hard Link로 나뉜다.
- 심볼 링크는 바로가기다.
- 하드 링크는 별칭을 가진 복사본 파일이 만들어 진다. 수정 내역을 서로 공유한다.

- ln -s test1.txt test1.ln (test1.txt에 대한 test1.ln 링크 파일 생성)

- -s 옵션이 없으면 하드 링크로 만들어 진다.
- 일반적으로 링크는 심볼릭 링크를 사용한다.

**링크파일을 이용한 실행파일 리졸빙**
- jdk를 설치했는데, java를 실행할떄마다 모두 경로를 적어줘야하는 문제가 있다. 심지어 java가 존재하는 폴더에서도
- echo $PATH로 명령어를 찾아보는 경로들을 모두 확인해 볼 수 있다.
- path에 선언되어있는 디렉토리에 링크파일을 만들면 경로 지정 없이 실행할 수 있다.

### 사용자 추가하기
- useradd : 사용자추가
	- useradd dragon
- usermod : 사용자변경 (modify)
- userdel : 사용자 삭제

- 추가된 사용자 확인하기 cat /etc/passwd (etc는 설정파일들을 담는 디렉토리), 또는 tail -n /etc/passwd
- sudo passwd dragon : dragon유저의 비밀번호 설정하기

### 홈 디렉토리 생성과 소유권 변경하기
- ls -l 하면 나오게 표시되는 정보중에 3번째는 소유자 정보, 4번째는 소유자 그룹 정보를 나타낸다. 아래는 root가 소유자고 root 그룹이 소유자 그룹이다.
```
drwxr-xr-x 3 root root 4096 Jul 14 2020 dragon
```

- sudo chown dragon ../dragon (change owner) : dragon에게 ../dragon 디렉토리 소유권한을 준다.
- sudo chown dragon:dragon ../dragon : dragon과 dragon 그룹에게 소유 권한을 준다.

### 사용자를 추가하는 스크립트 파일 생성하기
- ~/bin/adduser 에 아래와 같은 내용을 추가한다.
```
useradd testuser
tail -n2 /etc/passwd
mkdir /home/testuser
chown testuser:testuser /home/testuser
echo "testuser user added"
``` 
- 실행시에 파일의 경로를 지정해주지 않으면 $PATH에 있는 실행파일들을 먼저 뒤지기 떄문에 파일 경로를 지정해주자. ($ ./adduser)
- 경로를 지정해주고 싶지 않다면 $PATH 경로에 이는 디렉토리로 옮기자.
- adduser 라는 명령어가 중복된다면 가장 먼저 선언된 adduser명령어가 실행된다.
	- whereis adduser (adduser 명령어가 있는 경로들)
	- which adduser (현재 유저권한으로 실행하게 되는 adduser 명령어의 경로)
	- sudo which adduser (슈퍼 유저 권한으로 실행하개 되는 adduser 명렁어 경로)

### 파일권한 변경 (chmod, whereis)
- ls -l 하면 나오는 파일 권한들은 3비트씩 소유자(user), 그룹(group), 기타((other)에 대한 권한을 나타낸다. 
- 예를들어 -rwxr-xr-x test.txt 인 경우 test.txt의 소유자 권한은 READ, WRITE, EXECUTE권한이 모두 있고, 그룹과 기타는 읽기와 쓰기권한만 있다.
- 각 비트를 10진수로 변환하여 숫자로 써 나타낼 수 있다.
- chmod : 파일 권한 변경
	- chmod 644 test.txt (rw-r--r-- 로 설정된다.)
	- chmod u+x texst.txt (user에게 실행권한 추가)
	- chmod a+rwx test.txt (All 모두에게 모든 권한 추가) 	 

### 인자를 이용한 스크립트 파일로 변경하기 ($1)
- $1, $2, $3 ... 은 첫번째 인자, 두번쨰 인자, 세번쨰 인자를 뜻한다.
	- adduser a b c (a가 첫번째, b가 두번쨰, c가 세번쨰 인자다.)



### 참고자료
- 리눅스 for 개발자 - 뉴렉처 https://www.youtube.com/watch?v=TZjB94sA3IU&list=PLq8wAnVUcTFU9zLWK-dHWrvTJ0PF8Y0Sf
