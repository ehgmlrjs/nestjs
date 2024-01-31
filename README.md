# 주제: NestJS를 활용한 사용자 인증과 권한 관리 시스템 구현

## 서버 구동 방법
```
npm install
```

* .evn파일 수정 (mysql 사용)
```
DB_HOST=localhost
DB_PORT=3306
DB_USERNAME=your_db_username
DB_PASSWORD=your_db_password
DB_NAME=your_db_name
DB_SYNC=true
EMAILADDRESS=your_email_address
EMAILPASSWORD=your_email_password
```

* 네이버메일smtp설정
![이미지](https://velog.velcdn.com/images/kwontae1313/post/c47ec999-1836-45ff-862a-6ee72b5a7021/image.png)


```
npm start
```
애플리케이션은 'http://localhost:8000' 에서 실행됩니다.

## 기능

### 1. user
* 회원가입
  
  * 이메일과 닉네임이 DB에 존재하는지 확인한 후 없으면 유저의 정보를 DB에 저장
 
* 관리자 계정 회원가입

  * 이메일과 닉네임이 DB에 존재하지 않으면 관리자 계정으로 저장

* 유저 목록 조회
  
  * 로그인 된 유저의 정보를 확인하고 관리자 계정이면 유저 목록 표시
  * 관리자 계정이 아니면 에러 메세지 출력

* 비밀번호 변경

  * 로그인 된 유저의 비밀번호와 입력받은 비밀번호가 맞는지 검증하고
  * 새로운 비밀번호를 입력받아 비밀번호 변경


****
### 2. auth
* 로그인

  * 입력받은 이메일과 비밀번호가 저장된 유저의 정보와 일치하면 jwt토큰 발급
  * 틀릴경우 에러메세지 출력 로그인 시도 가능 횟수 감소
  * 로그인 시도 횟수를 초과하여 시도할 경우 로그인 불가

****
### 3. mail
* 메일 전송

  * 이메일을 입력받아 임시 비밀번호 생성 후 메일로 전송
  * 유저의 비밀번호를 임시 비밀번호로 변경
  * 로그인 시도 횟수 초기화


