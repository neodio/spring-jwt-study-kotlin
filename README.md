# Spring Boot JWT Tutorial - kotlin 버전

강의 학습 내용 실습 자료 - kotlin 버전

- [Spring Boot JWT Tutorial](https://inf.run/iu6LZ)

- Spring Boot를 이용한 JWT 인증, 인가 구현
- Spring Security 기초
- 회원가입, 로그인, 권한 로직

#### h2-console
- http://localhost:8080/h2-console
- url: jdbc:h2:mem:testdb
- username: sa

## API
### hello api
```
GET http://localhost:8080/api/hello
Request


Response
hello
```

### authenticate
```
POST http://localhost:8080/api/authenticate
Request
{
    "username": "admin",
    "password": "admin"
}

Response
{
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImF1dGgiOiJST0xFX0FETUlOLFJPTEVfVVNFUiIsImV4cCI6MTc1MTY5MTY2OX0.yhc1ltKpV0K9zru30KcL7-HITviuuQ_SuSWr8y8wDQZr7MNrOCLDSknohYJXxfq-LyfrfNtPXK4LPKZi2AfMgg"
}
```
<img src="image/postman.png"  width="450"/>

```
var jsonData = JSON.parse(responseBody);
pm.globals.set("jwt_tutorial_token", jsonData.token);
```
위와 같이 입력하면 postman에서 글로벌 변수로 활용 가능
<img src="image/global.png"  width="450"/>

### signUp
```
POST http://localhost:8080/api/signup
Request
{
    "username": "test",
    "password": "test",
    "nickname": "testName"
}

Response
{
    "username": "test",
    "nickname": "testName",
    "authorityDtoSet": [
        {
            "authorityName": "ROLE_USER"
        }
    ]
}
```

### getUser
```
GET http://localhost:8080/api/user/test
Request

Response
{
    "username": "test",
    "nickname": "testName",
    "authorityDtoSet": [
        {
            "authorityName": "ROLE_USER"
        }
    ]
}
```