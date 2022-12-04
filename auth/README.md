# 회원 인증(Auth)

### 1. 회원가입 <a href="#undefined" id="undefined"></a>

#### 1.1. 성공 201 <a href="#undefined" id="undefined"></a>

**http-request**

```java
POST /auth HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 121
Host: docs.api.com

{
  "email" : "user@test.com",
  "password" : "passWORD123!",
  "nickname" : "testUser1",
  "authKey" : "11111111"
}
```

| Path       | Type     | Description    |
| ---------- | -------- | -------------- |
| `email`    | `String` | valid email    |
| `password` | `String` | valid password |
| `nickname` | `String` | valid nickname |
| `authKey`  | `String` | auth key       |

**http-response**

```
HTTP/1.1 201 Created
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
Content-Length: 135

{
  "accessToken" : "Bearer AccessToken",
  "refreshToken" : "Bearer RefreshToken",
  "avatarPath" : "http://image/image.jpg.com"
}
```

| Path           | Type     | Description                |
| -------------- | -------- | -------------------------- |
| `accessToken`  | `String` | set client’s local storage |
| `refreshToken` | `String` | set client’s cookie        |
| `avatarPath`   | `String` | profile image path         |

#### 1.2. 실패 400\_유효성 검사 <a href="#_-_400_-_" id="_-_400_-_"></a>

**http-request**

```
POST /auth HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 121
Host: docs.api.com

{
  "email" : "user@testtest",
  "password" : "passWORD123!",
  "nickname" : "testUser1",
  "authKey" : "11111111"
}
```

| Path       | Type     | Description   |
| ---------- | -------- | ------------- |
| `email`    | `String` | invalid email |
| `password` | `String` | password      |
| `nickname` | `String` | nickname      |
| `authKey`  | `String` | auth Key      |

**http-response**

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
Content-Length: 131

{
  "status" : 400,
  "code" : "400 BAD_REQUEST",
  "message" : null,
  "validation" : {
    "email" : "invalid email"
  }
}
```

#### 1.3. 실패 404\_인증키 <a href="#_-_404_" id="_-_404_"></a>

**http-request**

```
POST /auth HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 121
Host: docs.api.com

{
  "email" : "user@test.com",
  "password" : "passWORD123!",
  "nickname" : "testUser1",
  "authKey" : "11111111"
}
```

| Path       | Type     | Description                         |
| ---------- | -------- | ----------------------------------- |
| `email`    | `String` | valid email                         |
| `password` | `String` | valid password                      |
| `nickname` | `String` | valid nickname                      |
| `authKey`  | `String` | auth key is only valid for one hour |

**http-response**

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
Content-Length: 131

{
  "status" : 404,
  "code" : "INVALID_AUTH_KEY",
  "message" : "invalid auth key, check your email",
  "validation" : null
}
```

#### 1.4. 실패 409\_중복\_이메일 <a href="#_-_409_-_" id="_-_409_-_"></a>

**http-request**

```
POST /auth HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 121
Host: docs.api.com

{
  "email" : "user@test.com",
  "password" : "passWORD123!",
  "nickname" : "testUser1",
  "authKey" : "11111111"
}
```

| Path       | Type     | Description    |
| ---------- | -------- | -------------- |
| `email`    | `String` | exist email    |
| `password` | `String` | valid password |
| `nickname` | `String` | valid nickname |
| `authKey`  | `String` | auth Key       |

**http-response**

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
Content-Length: 105

{
  "status" : 409,
  "code" : "EMAIL_EXISTS",
  "message" : "EMAIL_EXISTS",
  "validation" : null
}
```

#### 1.5. 실패 409\_중복\_닉네임 <a href="#_-_409_-_" id="_-_409_-_"></a>

**http-request**

```
POST /auth HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 121
Host: docs.api.com

{
  "email" : "user@test.com",
  "password" : "passWORD123!",
  "nickname" : "testUser1",
  "authKey" : "11111111"
}
```

| Path       | Type     | Description    |
| ---------- | -------- | -------------- |
| `email`    | `String` | valid email    |
| `password` | `String` | valid password |
| `nickname` | `String` | 이미 존재하는 닉네임.   |
| `authKey`  | `String` | auth Key       |

**http-response**

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

### 2. 이메일 인증 메일 전송 <a href="#_-_-_-_" id="_-_-_-_"></a>

#### 2.1. 성공 201 <a href="#_-_201_2" id="_-_201_2"></a>

**http-request**

```
POST /auth/mail HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 33
Host: docs.api.com

{
  "email" : "user@test.com"
}
```

| Path    | Type     | Description                                               |
| ------- | -------- | --------------------------------------------------------- |
| `email` | `String` | the same email can only be verified once every 5 minutes. |

**http-response**

```
HTTP/1.1 201 Created
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
Content-Length: 4

true
```

#### 2.2. 실패 409\_시간 제한 <a href="#_-_409_-_" id="_-_409_-_"></a>

**http-request**

```
POST /auth/mail HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 33
Host: docs.api.com

{
  "email" : "user@test.com"
}
```

| Path    | Type     | Description                                               |
| ------- | -------- | --------------------------------------------------------- |
| `email` | `String` | the same email can only be verified once every 5 minutes. |

**http-response**

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
Content-Length: 170

{
  "status" : 409,
  "code" : "AUTH_KEY_ALREADY_EXISTS",
  "message" : "auth key already exists, you can only request once every 5 minutes",
  "validation" : null
}
```

#### 2.3. 실패 409\_이미 존재하는 이메일 <a href="#_-_409_-_-_" id="_-_409_-_-_"></a>

**http-request**

```
POST /auth/mail HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 33
Host: docs.api.com

{
  "email" : "user@test.com"
}
```

| Path    | Type     | Description |
| ------- | -------- | ----------- |
| `email` | `String` | 이미 존재하는 이메일 |

**http-response**

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
Content-Length: 105

{
  "status" : 409,
  "code" : "EMAIL_EXISTS",
  "message" : "EMAIL_EXISTS",
  "validation" : null
}
```

***

### 3. 이메일 인증 <a href="#undefined" id="undefined"></a>

#### 3.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

**http-request**

```
PUT /auth/mail HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 60
Host: docs.api.com

{
  "email" : "user@test.com",
  "authKey" : "11111111"
}
```

| Path      | Type     | Description  |
| --------- | -------- | ------------ |
| `authKey` | `String` | user authKey |
| `email`   | `String` | user email   |

**http-response**

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
Content-Length: 31

{
  "authKey" : "222222222"
}
```

| Path      | Type     | Description                                      |
| --------- | -------- | ------------------------------------------------ |
| `authKey` | `String` | set in user’s useState And send when requestJoin |

#### 3.2. 실패 404\_존재하지\_않음 <a href="#_-_404_-_" id="_-_404_-_"></a>

**http-request**

```
PUT /auth/mail HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 60
Host: docs.api.com

{
  "email" : "user@test.com",
  "authKey" : "11111111"
}
```

| Path      | Type     | Description     |
| --------- | -------- | --------------- |
| `authKey` | `String` | invalid authKey |
| `email`   | `String` | user email      |

**http-response**

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
Content-Length: 131

{
  "status" : 404,
  "code" : "INVALID_AUTH_KEY",
  "message" : "invalid auth key, check your email",
  "validation" : null
}
```

***

### 4. 닉네임 중복 확인 <a href="#_-_-_" id="_-_-_"></a>

#### 4.1. 성공 200 <a href="#_-_200_2" id="_-_200_2"></a>

**http-request**

```
POST /auth/nickname HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 32
Host: docs.api.com

{
  "nickname" : "testUser1"
}
```

| Path       | Type     | Description |
| ---------- | -------- | ----------- |
| `nickname` | `String` | 중복되지 않는 닉네임 |

**http-response**

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
Content-Length: 4

true
```

#### 4.2. 실패 400\_유효성 검사 <a href="#_-_400_-_-_2" id="_-_400_-_-_2"></a>

**http-request**

```
POST /auth/nickname HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 35
Host: docs.api.com

{
  "nickname" : "ㅋㅋㅋㅋ"
}
```

| Path       | Type     | Description                                        |
| ---------- | -------- | -------------------------------------------------- |
| `nickname` | `String` | 유효성 검사 실패, 닉네임은 null이거나 공백일 수 없으며 닉네임 규정을 충족해야합니다. |

**http-response**

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

#### 4.3. 실패 409\_닉네임 중복 <a href="#_-_409_-_" id="_-_409_-_"></a>

**http-request**

```
POST /auth/nickname HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 32
Host: docs.api.com

{
  "nickname" : "testUser1"
}
```

| Path       | Type     | Description    |
| ---------- | -------- | -------------- |
| `nickname` | `String` | 이미 존재하는 닉네임 요청 |

**http-response**

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

### 5. 로그인 <a href="#_" id="_"></a>

#### 5.1. 성공 201 <a href="#_-_201_3" id="_-_201_3"></a>

**http-request**

```
POST /auth/token HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 65
Host: docs.api.com

{
  "email" : "user@test.com",
  "password" : "passWORD123!"
}
```

| Path       | Type     | Description         |
| ---------- | -------- | ------------------- |
| `email`    | `String` | valid user email    |
| `password` | `String` | valid user password |

**http-response**

```
HTTP/1.1 201 Created
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
Content-Length: 136

{
  "accessToken" : "Bearer AccessToken",
  "refreshToken" : "Bearer RefreshToken",
  "avatarPath" : "http://image/image.jpg/test"
}
```

| Path           | Type     | Description                            |
| -------------- | -------- | -------------------------------------- |
| `accessToken`  | `String` | accessToken, set client’s LocalStorage |
| `refreshToken` | `String` | refreshToken, set client’s Cookie      |
| `avatarPath`   | `String` | profile image remote path              |

#### 5.2. 실패 401 잘못된 입력값 <a href="#_-_401_-_" id="_-_401_-_"></a>

**http-request**

```
POST /auth/token HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 65
Host: docs.api.com

{
  "email" : "user@test.com",
  "password" : "passWORD123!"
}
```

| Path       | Type     | Description                         |
| ---------- | -------- | ----------------------------------- |
| `email`    | `String` | Invalid email or not found email    |
| `password` | `String` | Invalid password or not found email |

**http-response**

```
HTTP/1.1 401 Unauthorized
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
Content-Length: 105

{
  "status" : 401,
  "code" : "INVALID_USER",
  "message" : "INVALID_USER",
  "validation" : null
}
```

**response-fields**

```
{
  "status" : 401,
  "code" : "INVALID_USER",
  "message" : "INVALID_USER",
  "validation" : null
}
```

***

### 6. 로그아웃 <a href="#_" id="_"></a>

#### 6.1. 성공 204 <a href="#_-_204" id="_-_204"></a>

**http-request**

```
DELETE /auth/token HTTP/1.1
RefreshToken: Bearer RefreshToken
Host: docs.api.com
```

**http-response**

```
HTTP/1.1 204 No Content
Vary: Origin
Vary: Access-Control-Request-Method
Vary: Access-Control-Request-Headers
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
Strict-Transport-Security: max-age=31536000 ; includeSubDomains
X-Frame-Options: DENY
```

#### 6.2. 실패 404 <a href="#_-_404" id="_-_404"></a>

**http-request**

```
DELETE /auth/token HTTP/1.1
RefreshToken: Bearer RefreshToken
Host: docs.api.com
```

**http-response**

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
Content-Length: 111

{
  "status" : 404,
  "code" : "TOKEN_NOT_FOUND",
  "message" : "TOKEN_NOT_FOUND",
  "validation" : null
}
```

**response-fields**

```
{
  "status" : 404,
  "code" : "TOKEN_NOT_FOUND",
  "message" : "TOKEN_NOT_FOUND",
  "validation" : null
}
```

### 7. 리프레시 토큰 갱신 <a href="#_-_-_" id="_-_-_"></a>

#### 7.1. 성공 201 <a href="#_-_201_4" id="_-_201_4"></a>

http-request

```
PUT /auth/token HTTP/1.1
RefreshToken: Bearer RefreshToken
Host: docs.api.com
```

http-response

```
HTTP/1.1 201 Created
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
Content-Length: 136

{
  "accessToken" : "Bearer AccessToken",
  "refreshToken" : "Bearer RefreshToken",
  "avatarPath" : "http://image/image.jpg/test"
}
```

| Path           | Type     | Description               |
| -------------- | -------- | ------------------------- |
| `accessToken`  | `String` | set client’s localStorage |
| `refreshToken` | `String` | set client’s cookie       |
| `avatarPath`   | `String` | user profile image        |

#### 7.2. 실패 401\_유효하지 않은 토큰 <a href="#_-_401_-_-_" id="_-_401_-_-_"></a>

http-request

```
PUT /auth/token HTTP/1.1
RefreshToken: Bearer RefreshToken
Host: docs.api.com
```

http-response

```
HTTP/1.1 401 Unauthorized
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
  "status" : 401,
  "code" : "EXPIRED_EXCEPTION",
  "message" : "expired token",
  "validation" : null
}
```

response-fields

```
{
  "status" : 401,
  "code" : "EXPIRED_EXCEPTION",
  "message" : "expired token",
  "validation" : null
}
```

#### 7.3. 실패 404\_존재하지 않는 토큰 <a href="#_-_404_-_-_" id="_-_404_-_-_"></a>

http-request

```
PUT /auth/token HTTP/1.1
RefreshToken: Bearer RefreshToken
Host: docs.api.com
```

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
Content-Length: 111

{
  "status" : 404,
  "code" : "TOKEN_NOT_FOUND",
  "message" : "TOKEN_NOT_FOUND",
  "validation" : null
}
```

response-fields

```
{
  "status" : 404,
  "code" : "TOKEN_NOT_FOUND",
  "message" : "TOKEN_NOT_FOUND",
  "validation" : null
}
```

***

### 8. 비밀번호 변경 <a href="#_-_" id="_-_"></a>

#### 8.1. 성공 200 <a href="#_-_200_3" id="_-_200_3"></a>

http-request

```
PATCH /auth/password HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 78
Host: docs.api.com

{
  "originalPassword" : "passWORD123!",
  "newPassword" : "passWORD321!"
}
```

| Path               | Type     | Description    |
| ------------------ | -------- | -------------- |
| `originalPassword` | `String` | 변경 전 패스워드      |
| `newPassword`      | `String` | 유효성 검사 실패 패스워드 |

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
Content-Length: 4

true
```

#### 8.2. 실패 409\_잘못된 패스워드 <a href="#_-_409_-_" id="_-_409_-_"></a>

http-request

```
PATCH /auth/password HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 77
Host: docs.api.com

{
  "originalPassword" : "passWORD123!",
  "newPassword" : "PASSWORD123"
}
```

| Path               | Type     | Description    |
| ------------------ | -------- | -------------- |
| `originalPassword` | `String` | 변경 전 패스워드      |
| `newPassword`      | `String` | 유효성 검사 실패 패스워드 |

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
Content-Length: 140

{
  "status" : 400,
  "code" : "400 BAD_REQUEST",
  "message" : null,
  "validation" : {
    "newPassword" : "invalid password"
  }
}
```

#### 8.3. 실패 409\_잘못된 패스워드 <a href="#_-_409_-_-_2" id="_-_409_-_-_2"></a>

http-request

```
PATCH /auth/password HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 78
Host: docs.api.com

{
  "originalPassword" : "passWORD123!",
  "newPassword" : "passWORD321!"
}
```

| Path               | Type     | Description       |
| ------------------ | -------- | ----------------- |
| `originalPassword` | `String` | 기존 패스워드(잘못된 값 입력) |
| `newPassword`      | `String` | 변경 희망 패스워드        |

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
Content-Length: 149

{
  "status" : 409,
  "code" : "MISMATCHED_PASSWORD",
  "message" : "mismatched password, check your original password",
  "validation" : null
}
```

***

### 9. 비밀번호 찾기\_이메일 인증 <a href="#_-_-_-_" id="_-_-_-_"></a>

#### 9.1. 성공 201\_이메일 전송 <a href="#_-_201_-_" id="_-_201_-_"></a>

http-request

```
POST /auth/password/support HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 33
Host: docs.api.com

{
  "email" : "user@test.com"
}
```

| Path    | Type     | Description |
| ------- | -------- | ----------- |
| `email` | `String` | user email  |

http-response

```
HTTP/1.1 201 Created
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
Content-Length: 4

true
```

#### 9.2. 실패 404\_존재하지 않는 이메일 <a href="#_-_404_-_-_" id="_-_404_-_-_"></a>

http-request

```
POST /auth/password/support HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 33
Host: docs.api.com

{
  "email" : "user@test.com"
}
```

| Path    | Type     | Description       |
| ------- | -------- | ----------------- |
| `email` | `String` | 존재하지 않는 유저 메일일 경우 |

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

#### 9.3. 실패 409\_5분내\_요청\_이력 <a href="#_-_409_5-_-_" id="_-_409_5-_-_"></a>

http-request

```
POST /auth/password/support HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 33
Host: docs.api.com

{
  "email" : "user@test.com"
}
```

| Path    | Type     | Description                      |
| ------- | -------- | -------------------------------- |
| `email` | `String` | 5분 내에 해당 이메일로 인증키를 요청한 이력이 있을 경우 |

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
Content-Length: 170

{
  "status" : 409,
  "code" : "AUTH_KEY_ALREADY_EXISTS",
  "message" : "auth key already exists, you can only request once every 5 minutes",
  "validation" : null
}
```

***

### 10. 비밀번호 찾기\_임시패스워드 발급 <a href="#_-_-_-_" id="_-_-_-_"></a>

#### 10.1. 성공 200\_이메일 전송 <a href="#_-_200_-_" id="_-_200_-_"></a>

http-request

```
POST /auth/password/recovery HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 60
Host: docs.api.com

{
  "email" : "user@test.com",
  "authKey" : "11111111"
}
```

| Path      | Type     | Description |
| --------- | -------- | ----------- |
| `email`   | `String` | 유저 이메일      |
| `authKey` | `String` | 인증키         |

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
Content-Length: 4

true
```

#### 10.2. 실패 400\_유효성 검사 <a href="#_-_400_-_-_3" id="_-_400_-_-_3"></a>

http-request

```
POST /auth/password/recovery HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 54
Host: docs.api.com

{
  "email" : "user@test.com",
  "authKey" : null
}
```

| Path      | Type     | Description |
| --------- | -------- | ----------- |
| `email`   | `String` | 이메일         |
| `authKey` | `Null`   | 인증키         |

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
    "authKey" : "must not be blank"
  }
}
```

#### 10.3. 실패 404\_존재하지 않는 인증키 <a href="#_-_404_-_-_" id="_-_404_-_-_"></a>

http-request

```
POST /auth/password/recovery HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 60
Host: docs.api.com

{
  "email" : "user@test.com",
  "authKey" : "11111111"
}
```

| Path      | Type     | Description |
| --------- | -------- | ----------- |
| `email`   | `String` | 유저 이메일      |
| `authKey` | `String` | 잘못된 인증키     |

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
Content-Length: 131

{
  "status" : 404,
  "code" : "INVALID_AUTH_KEY",
  "message" : "invalid auth key, check your email",
  "validation" : null
}
```

***

### 11. 회원탈퇴 <a href="#_" id="_"></a>

#### 11.1. 성공 204 <a href="#_-_204_2" id="_-_204_2"></a>

http-request

```
DELETE /auth HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 35
Host: docs.api.com

{
  "password" : "passWORD123!"
}
```

| Path       | Type     | Description                     |
| ---------- | -------- | ------------------------------- |
| `password` | `String` | 올바르지 않은 (database 등록값과 다른) 패스워드 |

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
Content-Length: 106

{
  "status" : 400,
  "code" : "ONLY_TEST_CODE",
  "message" : "BAD_REQUEST",
  "validation" : null
}
```

#### 11.2. 실패 400\_유효성 검사 <a href="#_-_400_-_-_4" id="_-_400_-_-_4"></a>

http-request

```
DELETE /auth HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 35
Host: docs.api.com

{
  "password" : "passWORD123!"
}
```

| Path       | Type     | Description                                   |
| ---------- | -------- | --------------------------------------------- |
| `password` | `String` | 패스워드 유효성 검사 실패 (null이거나 공백, 혹은 알 수 없는 문자열 오류) |

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
Content-Length: 106

{
  "status" : 400,
  "code" : "ONLY_TEST_CODE",
  "message" : "BAD_REQUEST",
  "validation" : null
}
```

#### 11.3. 실패 409\_잘못된 패스워드 <a href="#_-_409_-_-_3" id="_-_409_-_-_3"></a>

http-request

```
DELETE /auth HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 35
Host: docs.api.com

{
  "password" : "passWORD123!"
}
```

| Path       | Type     | Description                     |
| ---------- | -------- | ------------------------------- |
| `password` | `String` | 올바르지 않은 (database 등록값과 다른) 패스워드 |

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
Content-Length: 106

{
  "status" : 400,
  "code" : "ONLY_TEST_CODE",
  "message" : "BAD_REQUEST",
  "validation" : null
}
```
