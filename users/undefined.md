# 대시보드 조회

### 1. 대시보드 조회

#### 1.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

http-request

```
PATCH /users/profiles HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc5NCwiZXhwIjoxNjcwMDgxNTk0fQ.rkuwxsliY-6R7YxTYhE2lLoBxeFZoIhd04-kfXVQgzA
Content-Length: 188
Host: docs.api.com

{
  "nickname" : "testUser2",
  "infoMessage" : "아무말이나 적어야지~",
  "github" : "https://docs.api.com/",
  "blog" : "https://docs.api.com/",
  "jobType" : "DEVELOPER"
}
```

| Path          | Type     | Description |
| ------------- | -------- | ----------- |
| `nickname`    | `String` | 닉네임         |
| `infoMessage` | `String` | 자기소개        |
| `github`      | `String` | 깃허브 주소      |
| `blog`        | `String` | 블로그 주소      |
| `jobType`     | `String` | 직업          |

http-response

```
HTTP/1.1 200 OK
Vary: Origin
Vary: Access-Control-Request-Method
Vary: Access-Control-Request-Headers
Content-Type: application/json;charset=UTF-8
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
Strict-Transport-Security: max-age=31536000 ; includeSubDomains
X-Frame-Options: DENY
Content-Length: 190

{
  "nickname" : "testUser2",
  "infoMessage" : "아무말이나 적어야지~",
  "github" : "https://github.com/",
  "blog" : "https://7357.tistory.com/",
  "jobType" : "DEVELOPER"
}
```

| Path          | Type     | Description |
| ------------- | -------- | ----------- |
| `nickname`    | `String` | 수정 후 닉네임    |
| `infoMessage` | `String` | 수정 후 자기소개   |
| `github`      | `String` | 수정 후 깃허브 주소 |
| `blog`        | `String` | 수정 후 블로그 주소 |
| `jobType`     | `String` | 수정 후 직업     |

#### 1.2. 실패 400 <a href="#_-_400" id="_-_400"></a>

http-request

```
PATCH /users/profiles HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc5NCwiZXhwIjoxNjcwMDgxNTk0fQ.rkuwxsliY-6R7YxTYhE2lLoBxeFZoIhd04-kfXVQgzA
Content-Length: 191
Host: docs.api.com

{
  "nickname" : "ㅋㅋㅋㅋ",
  "infoMessage" : "아무말이나 적어야지~",
  "github" : "https://docs.api.com/",
  "blog" : "https://docs.api.com/",
  "jobType" : "DEVELOPER"
}
```

| Path          | Type     | Description                                |
| ------------- | -------- | ------------------------------------------ |
| `nickname`    | `String` | 유효하지 않은 닉네임(null 혹은 웹 어플리케이션 규칙에 맞지 않는 경우) |
| `infoMessage` | `String` | 유효성 검증 대상 아님                               |
| `github`      | `String` | 유효성 검증 대상 아님                               |
| `blog`        | `String` | 유효성 검증 대상 아님                               |
| `jobType`     | `String` | 유효하지 않은 직업(미리 협의된 대문자 상수만 가능, 혹은 null인 경우) |

http-response

```
HTTP/1.1 400 Bad Request
Vary: Origin
Vary: Access-Control-Request-Method
Vary: Access-Control-Request-Headers
Content-Type: application/json;charset=UTF-8
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
Strict-Transport-Security: max-age=31536000 ; includeSubDomains
X-Frame-Options: DENY
Content-Length: 137

{
  "status" : 400,
  "code" : "400 BAD_REQUEST",
  "message" : null,
  "validation" : {
    "nickname" : "invalid nickname"
  }
}
```

#### 1.3. 실패 404 <a href="#_-_404" id="_-_404"></a>

http-request

```
PATCH /users/profiles HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc5NCwiZXhwIjoxNjcwMDgxNTk0fQ.rkuwxsliY-6R7YxTYhE2lLoBxeFZoIhd04-kfXVQgzA
Content-Length: 188
Host: docs.api.com

{
  "nickname" : "testUser2",
  "infoMessage" : "아무말이나 적어야지~",
  "github" : "https://docs.api.com/",
  "blog" : "https://docs.api.com/",
  "jobType" : "DEVELOPER"
}
```

| Path          | Type     | Description |
| ------------- | -------- | ----------- |
| `nickname`    | `String` | 닉네임         |
| `infoMessage` | `String` | 자기소개        |
| `github`      | `String` | 깃허브 주소      |
| `blog`        | `String` | 블로그 주소      |
| `jobType`     | `String` | 직업          |

http-response

```
HTTP/1.1 404 Not Found
Vary: Origin
Vary: Access-Control-Request-Method
Vary: Access-Control-Request-Headers
Content-Type: application/json;charset=UTF-8
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
Strict-Transport-Security: max-age=31536000 ; includeSubDomains
X-Frame-Options: DENY
Content-Length: 145

{
  "status" : 404,
  "code" : "USER_NOT_FOUND",
  "message" : "The user is a user who has left or does not exist.",
  "validation" : null
}
```

#### 1.4. 실패 409 <a href="#_-_409" id="_-_409"></a>

http-request

```
PATCH /users/profiles HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc5NCwiZXhwIjoxNjcwMDgxNTk0fQ.rkuwxsliY-6R7YxTYhE2lLoBxeFZoIhd04-kfXVQgzA
Content-Length: 188
Host: docs.api.com

{
  "nickname" : "testUser2",
  "infoMessage" : "아무말이나 적어야지~",
  "github" : "https://docs.api.com/",
  "blog" : "https://docs.api.com/",
  "jobType" : "DEVELOPER"
}
```

| Path          | Type     | Description |
| ------------- | -------- | ----------- |
| `nickname`    | `String` | 닉네임         |
| `infoMessage` | `String` | 자기소개        |
| `github`      | `String` | 깃허브 주소      |
| `blog`        | `String` | 블로그 주소      |
| `jobType`     | `String` | 직업          |

http-response

```
HTTP/1.1 409 Conflict
Vary: Origin
Vary: Access-Control-Request-Method
Vary: Access-Control-Request-Headers
Content-Type: application/json;charset=UTF-8
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
Strict-Transport-Security: max-age=31536000 ; includeSubDomains
X-Frame-Options: DENY
Content-Length: 111

{
  "status" : 409,
  "code" : "NICKNAME_EXISTS",
  "message" : "nickname exists",
  "validation" : null
}
```

***
