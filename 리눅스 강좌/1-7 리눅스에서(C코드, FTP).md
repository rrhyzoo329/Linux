# 리눅스 강좌
[:link: 리눅스 강좌 ](https://youtu.be/uRZr35xIBqg) 


<br>

### 리눅스에서(C코드, FTP)사용
## 리눅스에서 c언어 코딩
>1. gcc 컴파일러 설치 확인 
>2. 설치가 안되어 있다면 gcc 설치 => yum -y install gcc
>3. vi 오픈 (vi t.c) => t라는 c 파일 생성
>4. 행번호 :se nu
>5. c언어 입력
#include <stdio.h>
int main(void)
{
        puts("재밌는 리눅스 \n");
        return 0;
}
>6. :w > :wq
>7. 실행(gcc t.c) : t.c 파일 컴파일하기 > ls > ./a.out : a.out을 실행
![image](https://user-images.githubusercontent.com/93310395/169345816-21420510-42d2-456e-94c1-7d4404cdff40.png)

* a.out으로 입력하면 command not found 오류 => 현재 디렉터리 표시 ./ 
해줘야함 
    * ./를 입력하지 않으려면(로그아웃시 초기화)
        1) echo $PATH : 경로 확인하기 
        /usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/home/j/.local/bin:/home/j/bin
        2) PATH=$PATH: => 뒤에 . 추가 => PATH=$PATH:.
        3) 다시 경로 확인 
        /usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/home/j/.local/bin:/home/j/bin:.
        =>경로 마지막에 . 가 추가된것을 확인 할 수 있음

>8. -o 옵션 
* gcc t.c -o aa 
    * aa를 실행해도 t.c와 같은 내용이 출력
    
    ![image](https://user-images.githubusercontent.com/93310395/169347238-33f9f71e-3b53-463b-afef-35c0ff422041.png)


<br>


## 리눅스에서 FTP 사용
* ftp로 공개 ftp 서버에 접속 > 파일 다운로드
>1. ftp 설치 확인  : rpm -qa | grep ftp / yum -y install ftp
>2. 임시 디렉터리 만들기 : mkdir down
>3. 임시 디렉터리 접근 : cd down
>4. ftp에 실행 
* ftp에서 사용할 수 있는 명령어 리스트 : ftp > ? 
    * get  : 파일을 가져올 때
    * mget : 여러개 파일을 가져올 때 
    * put  : 파일 업로드
    * mput : 여러개 파일 업로드   

![image](https://user-images.githubusercontent.com/93310395/169443340-104c631c-88eb-4a58-b286-89eb9cdf4abe.png)

>5. ftp 연결 : ftp > open => 연결 주소 입력 => 이름입력 => 비밀번호 입력(없을시 enter)
- 입력 예시 : ftp > open => ftp.kaist.ac.kr => ftp => 비밀번호 없음

![image](https://user-images.githubusercontent.com/93310395/169445812-6b22e2e5-0e33-4ad6-b787-962a880874ad.png)

>6. 특정 파일 다운로드 => 다운로드 확인 및 종료 
- 입력 예시 : cd apache => cd httpd => pwd => ls =>  get httpd-2.4.53.tar.gz =>!ls => by 

* !ls : 다운로드 리스트 확인 
* by : 접속 연결 끊기 

![image](https://user-images.githubusercontent.com/93310395/169445876-0595ed3a-58b0-4e6a-8050-a64c3a6749d3.png)

![image](https://user-images.githubusercontent.com/93310395/169445942-29ece57d-9e9d-47b1-a954-73c12622ae41.png)


<br>


## 리눅스에서 압축 & 압출 풀기 
>1. 용량이 큰 파일 복사 하기  : cp /etc/services y
* 파일 크기 확인 ls -lh

# 파일 압축 하기
>1. 압축하기  : gzip 파일명 / xz 파일명 
>2. 압축 확인

![image](https://user-images.githubusercontent.com/93310395/169448200-7865c36f-4871-4b9e-a67d-8a7b0096b0ab.png)


<br>


# 파일 압축 풀기
>1. 압출 풀기 : gunzip 파일명.gz / unxz 파일명.xz 
>2. 압축 확인

![image](https://user-images.githubusercontent.com/93310395/169448302-43b676c0-a0cd-4c1a-b469-0d9aa837f4df.png)

* 압축률이 높을 시 속도가 느리고 압축률이 낮을 시 속도가 빠름 


<br>


# tar 압축 & 풀기 각각 진행

>1. 압출 풀기 > 묶여 있는 파일 풀기 => tar xf 파일명.tar
- 예시 : gunzip httpd-2.4.53.tar.gz > ls-lh > tar xf httpd-2.4.53.tar > 디렉토리 생성

![image](https://user-images.githubusercontent.com/93310395/169450871-2a819c3d-8afc-4afe-aef6-21447c003dfd.png)


>2. 풀려있는 파일 다시 묶기 => tar cf tar명 디렉토리명 > 압축하기 
- 예시 : du -sh httpd-2.4.53 > tar cf h.tar httpd-2.4.53
* du -sh : 디렉터리 용량 확인

![image](https://user-images.githubusercontent.com/93310395/169450936-a2d8394c-39f9-4324-889a-eb9ac4496878.png)

<br>

# tar 압축 & 풀기 동시 실행

>1. 묶고 압축하기 => tar cfz 압출파일명.gz 디렉토리명
- 예시 : tar cfz hh.tar.gz httpd-2.4.53

![image](https://user-images.githubusercontent.com/93310395/169452127-b7d33ca5-701e-4c78-b1d2-b7236b7e33a2.png)

>2. 풀고 압축 => tar xfz 압축명.gz
- 예시 : tar xfz hh.tar.gz

![image](https://user-images.githubusercontent.com/93310395/169452370-d40d3061-ba9e-46bb-aa92-3780ef54a0e3.png)


``` 