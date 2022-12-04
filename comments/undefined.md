# 게시글 댓글

### 1. 게시글에 대한 댓글 등록 <a href="#_-_-_-_" id="_-_-_-_"></a>

#### 1.1. 성공 201 <a href="#_-_201" id="_-_201"></a>

http-request

```
POST /articles/1/comments HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 54
Host: localhost:8080

{
  "content" : "유효한 댓글내용입니다."
}
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
X-Frame-Options: DENY
Content-Length: 400

[ {
  "commentId" : 1,
  "articleId" : 1,
  "answerId" : null,
  "content" : "냥냐냥냐",
  "userInfo" : {
    "userId" : 1,
    "nickname" : "NICKNAME",
    "grade" : "GOLD"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "FILENAME",
    "remotePath" : "FILEPATH"
  },
  "createdAt" : "2022-12-04T00:03:06.6914157",
  "lastModifiedAt" : "2022-12-04T00:03:06.6914157"
} ]
```

response-body

```
[ {
  "commentId" : 1,
  "articleId" : 1,
  "answerId" : null,
  "content" : "냥냐냥냐",
  "userInfo" : {
    "userId" : 1,
    "nickname" : "NICKNAME",
    "grade" : "GOLD"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "FILENAME",
    "remotePath" : "FILEPATH"
  },
  "createdAt" : "2022-12-04T00:03:06.6914157",
  "lastModifiedAt" : "2022-12-04T00:03:06.6914157"
} ]
```

| Path                   | Type     | Description    |
| ---------------------- | -------- | -------------- |
| `[].userInfo.userId`   | `Number` | 유저 식별자입니다      |
| `[].userInfo.nickname` | `String` | 유저 닉네임입니다      |
| `[].userInfo.grade`    | `String` | 유저 등급입니다       |
| `[].avatar.avatarId`   | `Number` | 프로필사진 식별자입니다   |
| `[].avatar.filename`   | `String` | 파일 이름입니다       |
| `[].avatar.remotePath` | `String` | 유저 닉네임입니다      |
| `[].articleId`         | `Number` | 글 식별자입니다       |
| `[].answerId`          | `Null`   | 비어있는 답글 식별자입니다 |
| `[].content`           | `String` | 댓글 내용입니다       |
| `[].commentId`         | `Number` | 댓글 식별자입니다      |
| `[].createdAt`         | `String` | 댓글 첫 작성일입니다.   |
| `[].lastModifiedAt`    | `String` | 댓글 최신 수정일입니다   |

### 2. 실패 400 <a href="#_-_400" id="_-_400"></a>

http-request

```
POST /articles/1/comments HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 24
Host: localhost:8080

{
  "content" : null
}
```

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
X-Frame-Options: DENY
Content-Length: 137

{
  "status" : 400,
  "code" : "400 BAD_REQUEST",
  "message" : null,
  "validation" : {
    "content" : "must not be blank"
  }
}
```

| Path      | Type   | Description             |
| --------- | ------ | ----------------------- |
| `content` | `Null` | 댓글이 비어 있으므로 등록될 수 없습니다. |

| Name            | Description  |
| --------------- | ------------ |
| `Authorization` | access token |

response-body

```
{
  "status" : 400,
  "code" : "400 BAD_REQUEST",
  "message" : null,
  "validation" : {
    "content" : "must not be blank"
  }
}
```

### 3. 게시글에 대한 댓글 수정 <a href="#_-_-_-_" id="_-_-_-_"></a>

```
PATCH /articles/1/comments/1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 68
Host: localhost:8080

{
  "content" : "유효한 길이의 댓글 콘텐트입니다."
}
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
Content-Length: 435

[ {
  "commentId" : 1,
  "articleId" : 1,
  "answerId" : null,
  "content" : "유효한 댓글내용입니다.",
  "userInfo" : {
    "userId" : 1,
    "nickname" : "testUser1",
    "grade" : "GOLD"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "randomfilename",
    "remotePath" : "randomremotepath"
  },
  "createdAt" : "2022-12-04T00:03:06.8869032",
  "lastModifiedAt" : "2022-12-04T00:03:06.8869032"
} ]
```

request-body

```
{
  "content" : "유효한 길이의 댓글 콘텐트입니다."
}
```

| Path      | Type     | Description |
| --------- | -------- | ----------- |
| `content` | `String` | 댓글 내용       |

| Name            | Description  |
| --------------- | ------------ |
| `Authorization` | access token |

response-body

```
[ {
  "commentId" : 1,
  "articleId" : 1,
  "answerId" : null,
  "content" : "유효한 댓글내용입니다.",
  "userInfo" : {
    "userId" : 1,
    "nickname" : "testUser1",
    "grade" : "GOLD"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "randomfilename",
    "remotePath" : "randomremotepath"
  },
  "createdAt" : "2022-12-04T00:03:06.8869032",
  "lastModifiedAt" : "2022-12-04T00:03:06.8869032"
} ]
```

| Path                   | Type     | Description    |
| ---------------------- | -------- | -------------- |
| `[]`                   | `Array`  | 응답 데이터         |
| `[].userInfo.userId`   | `Number` | 유저 식별자입니다      |
| `[].userInfo.nickname` | `String` | 유저 닉네임입니다      |
| `[].userInfo.grade`    | `String` | 유저 등급입니다       |
| `[].avatar.avatarId`   | `Number` | 프로필사진 식별자입니다   |
| `[].avatar.filename`   | `String` | 파일 이름입니다       |
| `[].avatar.remotePath` | `String` | 유저 닉네임입니다      |
| `[].articleId`         | `Number` | 글 식별자입니다       |
| `[].answerId`          | `Null`   | 비어있는 답글 식별자입니다 |
| `[].content`           | `String` | 댓글 내용입니다       |
| `[].commentId`         | `Number` | 댓글 식별자입니다      |
| `[].createdAt`         | `String` | 댓글 첫 작성일입니다.   |
| `[].lastModifiedAt`    | `String` | 댓글 최신 수정일입니다   |

```
PATCH /articles/1/comments/1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 68
Host: localhost:8080

{
  "content" : "유효한 길이의 댓글 콘텐트입니다."
}
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
Content-Length: 126

{
  "status" : 409,
  "code" : "CANNOT_ACCESS_COMMENT",
  "message" : "unable to access comment",
  "validation" : null
}
```

request-body

```
{
  "content" : "유효한 길이의 댓글 콘텐트입니다."
}
```

| Path      | Type     | Description |
| --------- | -------- | ----------- |
| `content` | `String` | 댓글 내용       |

| Name            | Description             |
| --------------- | ----------------------- |
| `Authorization` | 권한 없는 사용자의 access token |

response-body

```
{
  "status" : 409,
  "code" : "CANNOT_ACCESS_COMMENT",
  "message" : "unable to access comment",
  "validation" : null
}
```

### 4. 게시글에 대한 댓글 삭제 <a href="#_-_-_-_" id="_-_-_-_"></a>

#### 4.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

http-request

```
DELETE /articles/1/comments/1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 68
Host: localhost:8080

{
  "content" : "유효한 길이의 댓글 콘텐트입니다."
}
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
Content-Length: 435

[ {
  "commentId" : 2,
  "articleId" : 1,
  "answerId" : null,
  "content" : "살아남을 코멘트입니다.",
  "userInfo" : {
    "userId" : 1,
    "nickname" : "testUser1",
    "grade" : "GOLD"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "randomfilename",
    "remotePath" : "randomremotepath"
  },
  "createdAt" : "2022-12-04T00:03:06.3218261",
  "lastModifiedAt" : "2022-12-04T00:03:06.3218261"
} ]
```

#### 4.2. 실패 409 <a href="#_-_409" id="_-_409"></a>

http-request

```
DELETE /articles/1/comments/1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 68
Host: localhost:8080

{
  "content" : "유효한 길이의 댓글 콘텐트입니다."
}
```

| Path      | Type     | Description |
| --------- | -------- | ----------- |
| `content` | `String` | 댓글 내용       |

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
Content-Length: 126

{
  "status" : 409,
  "code" : "CANNOT_ACCESS_COMMENT",
  "message" : "unable to access comment",
  "validation" : null
}
```

### 5. 게시글에 대한 댓글 조회 <a href="#_-_-_-_" id="_-_-_-_"></a>

#### 5.1. 성공 200 <a href="#_-_200_2" id="_-_200_2"></a>

http-request

```
GET /articles/1/comments HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 68
Host: localhost:8080

{
  "content" : "유효한 길이의 댓글 콘텐트입니다."
}
```

| Path      | Type     | Description |
| --------- | -------- | ----------- |
| `content` | `String` | 댓글 내용       |

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
Content-Length: 435

[ {
  "commentId" : 2,
  "articleId" : 1,
  "answerId" : null,
  "content" : "살아남을 코멘트입니다.",
  "userInfo" : {
    "userId" : 1,
    "nickname" : "testUser1",
    "grade" : "GOLD"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "randomfilename",
    "remotePath" : "randomremotepath"
  },
  "createdAt" : "2022-12-04T00:03:06.4619814",
  "lastModifiedAt" : "2022-12-04T00:03:06.4619814"
} ]
```

#### 5.2. 실패 409 <a href="#_-_409_2" id="_-_409_2"></a>

http-request

```
GET /articles/1/comments HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 68
Host: localhost:8080

{
  "content" : "유효한 길이의 댓글 콘텐트입니다."
}
```

| Path      | Type     | Description |
| --------- | -------- | ----------- |
| `content` | `String` | 댓글 내용       |

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
Content-Length: 126

{
  "status" : 409,
  "code" : "CANNOT_ACCESS_COMMENT",
  "message" : "unable to access comment",
  "validation" : null
}
```
