# CTF

25-4 CTF 개념 정리 - 시나리오

## 시나리오 1번

모 서버 장악 후, 내부에 저장된 정보 확인.

**힌트**
```
1. 업로드 경로 확인
 - 임의의 파일 업로드 해보기

2. 웹 쉘 업로드 후 소스코드
   <?php system($_GET['cmd']); ?>

   Day2 파일 업로드 취약점 실습 내용
       - 1) 확장자를 우회) php -> phar, phtml 등등
       - 2) .htaccess(아파치 서버 설정 파일) 업로드 후 확장자 저장 설정 변경
             AddType application/x-httpd-php .abc .txt .xyz 등
       - vi .htaccess (.으로 시작되는 파일은 기본적으로 숨김처리 되어있음.
         view - show hidden files 체크 혹은 ls -al

3. 웹 쉘 업로드 성공 후 시스템 명령어로 flag 확인 (cat flag.php X, flag가 들어간 파일)
  - find / -name "flag*"

4.  /etc/passwd 파일
  - john the reaper (패스워드 크랙 툴)로 패스워드 알아내보기 : 크랙 하고자하는 문자열을 vi로 텍스트 파일로 저장.
  - john 파일명
리눅스 : /etc/passwd : 사용자 패스워드 정보를 가지고 있음.

5. setuid가 적용된 파일 찾기 : 인터넷 검색 활용
  - ssh 접속 명령어 : ssh id@ip
  - find / -perm ~
  - /bin/bash : 배시 쉘(터미널 쉘)로 변경

6. SetUID : 리눅스 특수 권한 파일을 실행 시에만 root 권한 획득
  - cat으로 실행시키지 말고, 해당 경로에서 ./프로그램 명으로 실행해보기
  - 커맨드 인젝션 - 권한 상승(LPE) - root 권한 획득 시, flag 값을 확인 가능
  - 명령어 이어서 쓸 때 ; 을 이용했던 것을 기억  ex) ls ; pwd
  - 특수 권한 SetUID: 파일을 실행할 때에만 파일 소유자 권한(root)을 획득할 수 있는 특수권한

7. root 계정으로 실행했던 명령어 로그 : bash history 확인

```

**kali linux 프록시 설정 끄는 법**

1. Web Browser
2. 우측 상단 햄버거 기호 클릭
3. Preferences
4. Proxy 검색
5. settings No Proxy로 바꾼 후 접속

**시나리오 흐름도**

1. 파일 업로드 기능 확인
2. 확장자 우회
3. 서버 장악
4. 계정 탈취
5. 공격 벡터 확인
6. 권한 상승
7. 정보 수집

### 1) 업로드가 가능한 경로

***

### 2) 특정파일의 확장자 확인

***
### 3) 웹 쉘 업로드 및 파일 확인

***
### 4) 서버 특정 사용자 패스워드 획득

***
### 5) 서버 내 setuid 적용된 파일 확인

SSH 접속 후, dumb shell을 bash shell로 전환
```
/bin/bash
```

쓸모없는 파일 제외하고 보기 기능
```
2>/dev/null
```

***
### 6) root 권한 획득


***
### 7) 

***

## 시나리오 2번
