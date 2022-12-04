# 포인트(Points)

### 1. 유저 잔여포인트 조회 <a href="#_-_-_" id="_-_-_"></a>

#### 1.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

http-request

```
GET /users/points HTTP/1.1
Authorization: Valid access token
Host: docs.api.com
```

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
Content-Length: 65

{
  "userId" : 1,
  "nickname" : "nickname",
  "point" : 10
}
```

| Path       | Type     | Description   |
| ---------- | -------- | ------------- |
| `userId`   | `Number` | 조회하는 유저 아이디   |
| `nickname` | `String` | 조회하는 유저 닉네임   |
| `point`    | `Number` | 조회하는 유저 잔여포인트 |

#### 1.2. 실패 404 존재하지 않는 유저 <a href="#_-_404_-_-_" id="_-_404_-_-_"></a>

http-request

```
GET /users/points HTTP/1.1
Authorization: Invalid access token
Host: docs.api.com:8080
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
Content-Length: 109

{
  "status" : 404,
  "code" : "USER_NOT_FOUND",
  "message" : "USER_NOT_FOUND",
  "validation" : null
}
```
