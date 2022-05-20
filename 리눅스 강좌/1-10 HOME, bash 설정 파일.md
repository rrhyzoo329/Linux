# 리눅스 강좌
[:link: 리눅스 강좌 ](https://youtu.be/uRZr35xIBqg) 


<br>


### 리눅스 파일 분류 

## HOME, bash 설정 파일
* 실행 순서
   1. 로그인 
   2. /etc/profile
   2. /etc/profile.d/*.sh 
   3. home 디렉터리로 접근
   4. ~/.bash_profile(본) 와 ~/.bashrc (보조) 읽음 or /etc/basgrc ==> $PS1
   5. ~/bash_history
   6. ~/.bash_logout에 저장된 것을 실행 

* /etc/profile 과 .profile은 shell이 bash 쉘이 아니라도 로그인 시 적용, 
.bashrc와 .bash_login, .bash_profile은 bash 쉘로 로그인 되었을 경우만 적용

* /etc/profile : 시스템 사용자 전체에 적용할 쉘 환경 변수를 담고 있음

* /etc/profile.d : 사용자가 쉘에 로그인할 때 /etc/profile 파일에 의해서 /etc/profile.d 디렉토리에 있는 스크립트(.sh로 되어 있는)들이 for문을 통해 실행

* ~/.bash_profile 
    * 사용자 홈 디렉토리에 있음
    * 사용자의 .bashrc 를 읽어 실행되도록 할 뿐만 아니라 실행 경로 환경 변수를 적용 가능 
    * PATH=$SPATH:추가할경로:추가할경로

* ~/.bashrc : 
    * 사용자가 로그인하였을 때 ~/.bash_profile에 의해서 .bashrc 파일이 실행
    * 다시 .bashrc 파일에 의해서 /etc/bashrc 파일이 실행

* export : 전역변수를 지역변수화 시킴 
    - export 환경변수명 = 원하는 환경변수 

* source : 수정한 후 바로 적용하기 => source ~/.bash_prifile
    * source를 사용하지 않으면 재로그인이 필요 


<br>


## 출력 내용 저장 하기 
* >: 명령어 뒤에 나오는 파일에 쓸 때 사용(=write or overwrite)
    * rpm  -qa > rpmList => rpm 리스트 저장 

* >>: 명령어 뒤에 나오는 파일에 추가할 때 사용(=append)
     * cal >> rpmList => rpmList에 캘린더 추가 저장



``` 