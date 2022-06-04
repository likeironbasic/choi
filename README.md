---
### top명령어
---
#### top명령어는 현재 컴퓨터 부품들의 상황을 나타낼 수 있는 명령어다.
-이 명령은 USER, PID, %CPU, %MEM, VSZ, RSS, STAT, START, TTY, TIME 및 CMD 레이블이 지정된 열한 개에 정보를 표시할 수 있다.

-shift + p : CPU 사용률 내림차순

-shit + m : 메모리 사용률 내림차순

-shift + t : 프로세스가 돌아가고 있는 시간 순

-k : kill. k 입력 후 PID 번호 작성. signal은 9

-f : sort field 선택 화면 -> q 누르면 RES순으로 정렬

-a : 메모리 사용량에 따라 정렬

-b : Batch 모드로 작동

-1 : CPU Core별로 사용량을 보여줌


#### ps와 top의 차이점
-ps는 ps한 시점에 proc에서 검색한 cpu 사용량을 보여준다.

-top은 proc에서 일정 주기로 합산해 cpu 사용율 출력해준다.

[출처](https://zzsza.github.io/development/2018/07/18/linux-top/)

![top화면 캡쳐](https://user-images.githubusercontent.com/87355474/171950112-d8cb33d0-ed28-4891-845a-186f4ca39029.png)



---
### ps 명령어
---
#### ps명령어는 실행 중인 프로세스[PLD]를 확인할 수 있다.
-a: 다른 사용자들의 프로세스도 보여준다.

-u: 터미널이 다른 프로세스도 보여준다.

-x: 터미널이 없는 프로세스도 보여준다.

---
-ps ax : 동작중인 모든 프로세스를 확인

-ps aux : 동작중인 모든 프로세스를 소유자 정보와 함께 출력

-ps aux : grep [프로세스 이름] : 특정 프로세스에 대해서 보고 싶은 경우에 입력

-ps auxo pid,comm : PID 및 COMMAND에 대한 정보만 인쇄하려면 다음 명령 중 하나를 실행

-ps aux --sort=-%mem : 메모리 사용량을 기준으로 출력을 정렬하려면 다음을 사용

-ps -ef | grep [그룹] : 특정 사용자에 속하는 프로세스만 표시하려면 다음을 실행

[출처](https://cpm0722.github.io/system-programming/ps-command)

![image](https://user-images.githubusercontent.com/87355474/171952257-55f86d95-bff8-4f77-9d37-337e9d5bbbdf.png)



---
### jobs 명령어
---
#### jobs 명령어는 작업의 상태를 표시하는 명령어다. 현재 쉘 세련에서 실행시킨 백그라운드 작업의 목록이
#### 출력되며, 각 작업에는 번호가 붙어있어 kill 명령어 뒤에 '%번호' 등으로 사용할 수 있다.
- -l : 프로세스 그룹 id를 state필드 앞에 출력

- -n : 프로세스 그룹 중에 대표 프로세스 id를 출력

- -p : 각 프로세스 id에 대해 한 행씩 출력

- command : 지정한 명령어를 실행

- Running : 작업이 계속 진행중임

- Done : 작업이 완료되어 0을 반환

- Done(code) : 작업이 종료되었으며 0이 아닌 코드를 반환

- Stopped : 작업이 일시 중단

- Stopped(SIGSTP,SIGSTOP,SIGTTIN,SIGTTOU) 각 시그널이 작업을 일시 중단

[출처](https://hbase.tistory.com/265)

![image](https://user-images.githubusercontent.com/87355474/171955943-3586d6bc-486c-4a28-abc9-74e1072f31a7.png)



---
### kill 명령어
---
#### 프로세스에 시그널을 보내는 명령어(아래의 이미지는 시그널 리스트)
![image](https://user-images.githubusercontent.com/87355474/171956318-370e570f-d504-4be0-bd4b-204ef0a63372.png)

---
#### 많이 쓰이는 시그널들

|시그널|영어|설명|
|---|---|---|
|SIGHUP|Hang Up|세션이 종료될 때 시스템이 내리는 시그널|
|SIGINT|Interrupt|Ctrl + C, 종료 요청 시그널|
|SIGKILL|Kill|강제 종료 시그널|
|SIGSEGV|Segment Violation|메모리 침범이 일어날 때 시스템이 보내는 시그널|
|SIGTERM|Terminate|기본 값, 종료 요청 시그널|
|SIGTSTP|Temporary|Stop	Ctrl + Z 일시 중지 요청 시그널|

#### 프로세스에 시그널 보내는 법
```
$ kill [option] PID

#### 1234(PID) 프로세스 종료 

$ kill -9 dasdasdasdasdas
$ kill -SIGKILL dasdsadasdasdsa
```






---
### vim 에디터 매크로
---
#### q(저장 매크로)

- qA -> 작업 -> q
- q 로 시작해서 q로 끝난다
- 시작 q 다음은 매크로명
-   레코딩 끝난 후 기록된 내용 보려면 reg(ister)명령을 이용한다.
-   가령 위 예에서 매크로명을 'A'라고 했으니 ':reg A' 라고 한다

##### 매크로 실행
-  qA
-  3qA(3회반복)

##### 매크로 편집
- "Ap : 현재 커서 위치에 기록된 매크로 내용 표시

- "Ayy : 출력된 매크로 내용에서 작업 수정/추가 등을 한 후 편집한 내용 다시 등록

#### @(저장된 매크로 재생)
- @{레지스터} : 특정 레지스터에 저장된 매크로를 실행시킴

- @@ : 직전에 실행한 매크로를 재실행

