# 게시글 신고

#### 1.1. 성공 로그인한 회원이 게시글 신고 201 <a href="#_-_-_-_-_-_201" id="_-_-_-_-_-_201"></a>

HTTP request

```
POST /articles/1/reports HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 58
Host: localhost:8080

{
  "reason" : "BAD_LANGUAGE",
  "content" : "이유"
}
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

| Path      | Type     | Description               |
| --------- | -------- | ------------------------- |
| `reason`  | `String` | 신고 카테고리 내용입니다. 이넘으로 적어주세요 |
| `content` | `String` | 신고 사유입니다.                 |

HTTP response

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
Content-Length: 22

{
  "reportId" : 1
}
```

| Path       | Type     | Description |
| ---------- | -------- | ----------- |
| `reportId` | `Number` | 신고 아이디입니다.  |

#### 1.2. 실패 로그인한 회원이 존재하지 않는 게시글 신고 404 <a href="#_-_-_-_-_-_-_-_404" id="_-_-_-_-_-_-_-_404"></a>

HTTP request

```
POST /articles/500/reports HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 58
Host: localhost:8080

{
  "reason" : "BAD_LANGUAGE",
  "content" : "이유"
}
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

| Path      | Type     | Description               |
| --------- | -------- | ------------------------- |
| `reason`  | `String` | 신고 카테고리 내용입니다. 이넘으로 적어주세요 |
| `content` | `String` | 신고 사유입니다.                 |

HTTP response

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
Content-Length: 115

{
  "status" : 404,
  "code" : "ARTICLE_NOT_FOUND",
  "message" : "ARTICLE_NOT_FOUND",
  "validation" : null
}
```

#### 1.3. 실패 로그인하지 않은 회원이 게시글 신고 404 <a href="#_-_-_-_-_-_-_404" id="_-_-_-_-_-_-_404"></a>

HTTP request

```
POST /articles/500/reports HTTP/1.1
Content-Type: application/json;charset=UTF-8
Content-Length: 58
Host: localhost:8080

{
  "reason" : "BAD_LANGUAGE",
  "content" : "이유"
}
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

| Path      | Type     | Description               |
| --------- | -------- | ------------------------- |
| `reason`  | `String` | 신고 카테고리 내용입니다. 이넘으로 적어주세요 |
| `content` | `String` | 신고 사유입니다.                 |

HTTP response

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
