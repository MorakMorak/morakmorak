# 이미지 처리(Files)

### 1. 프로필 사진 업로드 URL 요청 <a href="#_-_-_-_url_" id="_-_-_-_url_"></a>

#### 1.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

http-request

```
GET /users/profiles/avatars HTTP/1.1
Authorization: AccessToken
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
X-Frame-Options: DENY
Content-Length: 89

{
  "avatarId" : 1,
  "preSignedUrl" : "https://aws.filename.png/secret=aD@!DSSFZcs"
}
```

| Path           | Type     | Description           |
| -------------- | -------- | --------------------- |
| `avatarId`     | `Number` | 등록된 avatarId          |
| `preSignedUrl` | `String` | 해당 경로로 파일을 업로드해야 합니다. |

#### 1.2. 실패 404 <a href="#_-_404" id="_-_404"></a>

데이터베이스에서 유저 정보를 찾을 수 없음.

http-request

```
GET /users/profiles/avatars HTTP/1.1
Authorization: AccessToken
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
X-Frame-Options: DENY
Content-Length: 145

{
  "status" : 404,
  "code" : "USER_NOT_FOUND",
  "message" : "The user is a user who has left or does not exist.",
  "validation" : null
}
```

#### 1.3. 실패 409 <a href="#_-_409" id="_-_409"></a>

AWS S3와의 연결 문제로 인한 실패.

http-request

```
GET /users/profiles/avatars HTTP/1.1
Authorization: AccessToken
Host: docs.api.com
```

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
X-Frame-Options: DENY
Content-Length: 154

{
  "status" : 409,
  "code" : "CAN_NOT_ACCESS_S3",
  "message" : "unable to access amazon s3, contract your administrator.",
  "validation" : null
}
```

***

### 2. 게시글 이미지 업로드 URL 요청 <a href="#_-_-_-_url_" id="_-_-_-_url_"></a>

#### 2.1. 성공 200 <a href="#_-_200_2" id="_-_200_2"></a>

http-request

```
GET /files HTTP/1.1
Authorization: AccessToken
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
X-Frame-Options: DENY
Content-Length: 87

{
  "fileId" : 1,
  "preSignedUrl" : "https://aws.filename.png/secret=aD@!DSSFZcs"
}
```

| Path           | Type     | Description           |
| -------------- | -------- | --------------------- |
| `fileId`       | `Number` | 등록된 file Id           |
| `preSignedUrl` | `String` | 해당 경로로 파일을 업로드해야 합니다. |

#### 2.2. 실패 409 <a href="#_-_409_2" id="_-_409_2"></a>

AWS S3와의 연결 문제로 인한 실패.

http-request

```
GET /files HTTP/1.1
Authorization: AccessToken
Host: docs.api.com
```

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
X-Frame-Options: DENY
Content-Length: 154

{
  "status" : 409,
  "code" : "CAN_NOT_ACCESS_S3",
  "message" : "unable to access amazon s3, contract your administrator.",
  "validation" : null
}
```

***

### 3. 프로필 이미지 삭제 <a href="#_-_-_" id="_-_-_"></a>

#### 3.1. 성공 204 <a href="#_-_204" id="_-_204"></a>

http-request

```
DELETE /users/profiles/avatars HTTP/1.1
Authorization: AccessToken
Host: docs.api.com
```

http-response

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
X-Frame-Options: DENY
```

#### 3.2. 실패 404 <a href="#_-_404_2" id="_-_404_2"></a>

유저의 이미지에 대한 정보를 Database에서 찾을 수 없음.

http-request

```
DELETE /users/profiles/avatars HTTP/1.1
Authorization: AccessToken
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
X-Frame-Options: DENY
Content-Length: 109

{
  "status" : 404,
  "code" : "FILE_NOT_FOUND",
  "message" : "FILE_NOT_FOUND",
  "validation" : null
}
```

#### 3.3. 실패 409 <a href="#_-_409_3" id="_-_409_3"></a>

AWS S3와의 연결 문제로 인한 실패.

http-request

```
DELETE /users/profiles/avatars HTTP/1.1
Authorization: AccessToken
Host: docs.api.com
```

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
X-Frame-Options: DENY
Content-Length: 154

{
  "status" : 409,
  "code" : "CAN_NOT_ACCESS_S3",
  "message" : "unable to access amazon s3, contract your administrator.",
  "validation" : null
}
```
