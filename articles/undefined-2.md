# 게시글 좋아요

#### 1.1. 성공 좋아요 등록 200 <a href="#_-_-_-_200" id="_-_-_-_200"></a>

http-request

```
POST /articles/1/likes HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

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
Content-Length: 81

{
  "articleId" : 1,
  "userId" : 1,
  "isLiked" : true,
  "likeCount" : 1
}
```

| Path        | Type      | Description                   |
| ----------- | --------- | ----------------------------- |
| `articleId` | `Number`  | 글의 아이디 입니다.                   |
| `userId`    | `Number`  | 유저의 아이디 입니다.                  |
| `isLiked`   | `Boolean` | 해당 유저가 좋아요를 눌렀는지 안눌렀지를 보여줍니다, |
| `likeCount` | `Number`  | 해당 게시글의 좋아요 숫자입니다.            |

#### 1.2. 성공 좋아요 취소 200 <a href="#_-_-_-_200" id="_-_-_-_200"></a>

http-request

```
POST /articles/1/likes HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

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
Content-Length: 81

{
  "articleId" : 1,
  "userId" : 1,
  "isLiked" : true,
  "likeCount" : 0
}
```

| Path        | Type      | Description                   |
| ----------- | --------- | ----------------------------- |
| `articleId` | `Number`  | 글의 아이디 입니다.                   |
| `userId`    | `Number`  | 유저의 아이디 입니다.                  |
| `isLiked`   | `Boolean` | 해당 유저가 좋아요를 눌렀는지 안눌렀지를 보여줍니다, |
| `likeCount` | `Number`  | 해당 게시글의 좋아요 숫자입니다.            |

#### 1.3. 실패 로그인하지 않은 유저가 좋아요를 누를때 404 <a href="#_-_-_-_-_-_-_404" id="_-_-_-_-_-_-_404"></a>

http-request

```
POST /articles/1/likes HTTP/1.1
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

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

#### 1.4. 실패 존재하지 않는 게시글의 좋아용를 누를때 404 <a href="#_-_-_-_-_-_-_404" id="_-_-_-_-_-_-_404"></a>

http-request

```
POST /articles/500/likes HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

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
Content-Length: 115

{
  "status" : 404,
  "code" : "ARTICLE_NOT_FOUND",
  "message" : "ARTICLE_NOT_FOUND",
  "validation" : null
}
```
