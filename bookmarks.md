# 북마크 (Bookmarks)

### 1. 북마크 등록/취소 <a href="#_-_201" id="_-_201"></a>

#### 1.1. 성공 201 <a href="#_-_201" id="_-_201"></a>

http-request

```
POST /articles/1/bookmark HTTP/1.1
Content-Type: application/json;charset=UTF-8
Accept: application/json
Authorization: AccessToken
Host: localhost:8080
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
Content-Length: 173

{
  "articleId" : 1,
  "userId" : 1,
  "scrappedByThisUser" : true,
  "createdAt" : "2022-12-03T01:03:57.5860906",
  "lastModifiedAt" : "2022-12-03T01:03:57.5870915"
}
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 북마크할 게시글의 식별자 |

| Name            | Description  |
| --------------- | ------------ |
| `Authorization` | access token |

response-body

```
{
  "articleId" : 1,
  "userId" : 1,
  "scrappedByThisUser" : true,
  "createdAt" : "2022-12-03T01:03:57.5860906",
  "lastModifiedAt" : "2022-12-03T01:03:57.5870915"
}
```

| Path                 | Type      | Description      |
| -------------------- | --------- | ---------------- |
| `articleId`          | `Number`  | 게시글 식별자          |
| `userId`             | `Number`  | 유저 식별자           |
| `scrappedByThisUser` | `Boolean` | 유저에게 스크랩되었는지 여부  |
| `createdAt`          | `String`  | 처음 북마크한 일자       |
| `lastModifiedAt`     | `String`  | 마지막으로 메모를 수정한 일자 |

#### 1.2. 실패 <a href="#_" id="_"></a>

http-request

```
POST /articles/3000/bookmark HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
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
Content-Length: 115

{
  "status" : 404,
  "code" : "ARTICLE_NOT_FOUND",
  "message" : "ARTICLE_NOT_FOUND",
  "validation" : null
}
```

| Parameter    | Description        |
| ------------ | ------------------ |
| `article-id` | 유효하지 않은 article Id |

| Name            | Description  |
| --------------- | ------------ |
| `Authorization` | access token |

response-body

```
{
  "status" : 404,
  "code" : "ARTICLE_NOT_FOUND",
  "message" : "ARTICLE_NOT_FOUND",
  "validation" : null
}
```
