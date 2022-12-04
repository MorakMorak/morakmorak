# 등록/수정/삭제/상세조회

## 1. 게시글 등록 <a href="#_-_" id="_-_"></a>

### 1.1. 성공 201 <a href="#_-_201" id="_-_201"></a>

http-request

```
POST /articles HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 347
Host: localhost:8080

{
  "title" : "안녕하세요 타이틀입니다. 잘 부탁드립니다. 타이틀은 신경씁니다.",
  "content" : "콘텐트입니다. 잘부탁드립니다.",
  "tags" : [ {
    "tagId" : 1,
    "name" : "JAVA"
  } ],
  "category" : "INFO",
  "fileId" : [ {
    "fileId" : 1
  }, {
    "fileId" : 2
  } ],
  "thumbnail" : 1
}
```

| Path              | Type     | Description     |
| ----------------- | -------- | --------------- |
| `title`           | `String` | 글의 제목입니다.       |
| `content`         | `String` | 글의 본문입니다.       |
| `tags[].tagId`    | `Number` | 태그 아이디 입니다.     |
| `tags[].name`     | `String` | 태그 이름입니다.       |
| `category`        | `String` | 글의 카테고리입니다.     |
| `fileId[].fileId` | `Number` | 파일 아이디 입니다.     |
| `thumbnail`       | `Number` | 글의 썸네일 아이디 입니다. |

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
Content-Length: 23

{
  "articleId" : 1
}
```

| Path        | Type     | Description |
| ----------- | -------- | ----------- |
| `articleId` | `Number` | 글의 아이디 입니다. |

#### 1.2. 실패 400 유효성 검증에 실패 <a href="#_-_400_-_-_" id="_-_400_-_-_"></a>

http-request

```
POST /articles HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 234
Host: localhost:8080

{
  "title" : "타이틀",
  "content" : "콘텐트",
  "tags" : [ {
    "tagId" : 1,
    "name" : "JAVA"
  } ],
  "category" : "INFO",
  "fileId" : [ {
    "fileId" : 1
  }, {
    "fileId" : 2
  } ],
  "thumbnail" : 1
}
```

| Path              | Type     | Description     |
| ----------------- | -------- | --------------- |
| `title`           | `String` | 글의 제목입니다.       |
| `content`         | `String` | 글의 본문입니다.       |
| `tags[].tagId`    | `Number` | 태그 아이디 입니다.     |
| `tags[].name`     | `String` | 태그 이름입니다.       |
| `category`        | `String` | 글의 카테고리입니다.     |
| `fileId[].fileId` | `Number` | 파일 아이디 입니다.     |
| `thumbnail`       | `Number` | 글의 썸네일 아이디 입니다. |

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
Content-Length: 213

{
  "status" : 400,
  "code" : "400 BAD_REQUEST",
  "message" : null,
  "validation" : {
    "title" : "size must be between 5 and 2147483647",
    "content" : "size must be between 5 and 2147483647"
  }
}
```

#### 1.3. 실패 404 존재하지 않는 태그 <a href="#_-_404_-_-_" id="_-_404_-_-_"></a>

http-request

```
POST /articles HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 347
Host: localhost:8080

{
  "title" : "안녕하세요 타이틀입니다. 잘 부탁드립니다. 타이틀은 신경씁니다.",
  "content" : "콘텐트입니다. 잘부탁드립니다.",
  "tags" : [ {
    "tagId" : 1,
    "name" : "JAVA"
  } ],
  "category" : "INFO",
  "fileId" : [ {
    "fileId" : 1
  }, {
    "fileId" : 2
  } ],
  "thumbnail" : 1
}
```

| Path              | Type     | Description     |
| ----------------- | -------- | --------------- |
| `title`           | `String` | 글의 제목입니다.       |
| `content`         | `String` | 글의 본문입니다.       |
| `tags[].tagId`    | `Number` | 태그 아이디 입니다.     |
| `tags[].name`     | `String` | 태그 이름입니다.       |
| `category`        | `String` | 글의 카테고리입니다.     |
| `fileId[].fileId` | `Number` | 파일 아이디 입니다.     |
| `thumbnail`       | `Number` | 글의 썸네일 아이디 입니다. |

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
Content-Length: 107

{
  "status" : 404,
  "code" : "TAG_NOT_FOUND",
  "message" : "TAG_NOT_FOUND",
  "validation" : null
}
```

***

## 2. 게시글 수정 <a href="#_-_" id="_-_"></a>

### 2.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

http-request

```
PATCH /articles/1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 270
Host: localhost:8080

{
  "title" : "타이틀입니다. 잘부탁드립니다. 부탁드립니다.",
  "content" : "콘텐트입니다. 잘부탁드립니다.",
  "tags" : [ {
    "tagId" : 1,
    "name" : "JAVA"
  } ],
  "fileId" : [ {
    "fileId" : 1
  } ],
  "thumbnail" : 1
}
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

| Path              | Type     | Description     |
| ----------------- | -------- | --------------- |
| `title`           | `String` | 글의 제목입니다.       |
| `content`         | `String` | 글의 본문입니다.       |
| `tags[].tagId`    | `Number` | 태그 아이디 입니다.     |
| `tags[].name`     | `String` | 태그 이름입니다.       |
| `fileId[].fileId` | `Number` | 파일 아이디 입니다.     |
| `thumbnail`       | `Number` | 글의 썸네일 아이디 입니다. |

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
Content-Length: 23

{
  "articleId" : 1
}
```

| Path        | Type     | Description |
| ----------- | -------- | ----------- |
| `articleId` | `Number` | 글의 아이디 입니다. |

#### 2.2. 실패 400 유효성 검증 <a href="#_-_400_-_" id="_-_400_-_"></a>

http-request

```
PATCH /articles/1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 184
Host: localhost:8080

{
  "title" : "타이틀",
  "content" : "콘텐트",
  "tags" : [ {
    "tagId" : 1,
    "name" : "JAVA"
  } ],
  "fileId" : [ {
    "fileId" : 1
  } ],
  "thumbnail" : 1
}
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

| Path              | Type     | Description     |
| ----------------- | -------- | --------------- |
| `title`           | `String` | 글의 제목입니다.       |
| `content`         | `String` | 글의 본문입니다.       |
| `tags[].tagId`    | `Number` | 태그 아이디 입니다.     |
| `tags[].name`     | `String` | 태그 이름입니다.       |
| `fileId[].fileId` | `Number` | 파일 아이디 입니다.     |
| `thumbnail`       | `Number` | 글의 썸네일 아이디 입니다. |

***

### 3. 게시글 삭제 <a href="#_-_" id="_-_"></a>

#### 3.1. 성공 204 <a href="#_-_204" id="_-_204"></a>

http-request

```
DELETE /articles/1 HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

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

#### 3.2. 실패 타인의 게시글을 삭제하려할때 403 <a href="#_-_-_-_-_403" id="_-_-_-_-_403"></a>

http-request

```
DELETE /articles/1 HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

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
X-Frame-Options: DENY
Content-Length: 105

{
  "status" : 401,
  "code" : "INVALID_USER",
  "message" : "INVALID_USER",
  "validation" : null
}
```

#### 3.3. 실패 존재하지 않는 게시글을 삭제할때 404 <a href="#_-_-_-_-_-_404" id="_-_-_-_-_-_404"></a>

http-request

```
DELETE /articles/1 HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |

http-response

```
HTTP/1.1 403 Forbidden
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
Content-Length: 129

{
  "status" : 403,
  "code" : "NO_ACCESS_TO_THAT_OBJECT",
  "message" : "no access to that object",
  "validation" : null
}
```

***

### 4. 게시글 상세조회 <a href="#_-_" id="_-_"></a>

#### 4.1. 성공 로그인한 회원이 게시글 상세 조회시 200 <a href="#_-_-_-_-_-_-_200" id="_-_-_-_-_-_-_200"></a>

http-request

```
GET /articles/1 HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description  |
| ------------ | ------------ |
| `article-id` | 게시글 아이디 입니다. |

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
Content-Length: 1169

{
  "articleId" : 1,
  "category" : "INFO",
  "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
  "content" : "콘탠트입니다. 제발 됬으면 좋겠습니다.",
  "clicks" : 10,
  "likes" : 1,
  "isClosed" : false,
  "isLiked" : true,
  "isBookmarked" : true,
  "tags" : [ {
    "tagId" : 1,
    "name" : "JAVA"
  } ],
  "createdAt" : "2022-12-04T00:02:53.899709",
  "lastModifiedAt" : "2022-12-04T00:02:53.899709",
  "expiredDate" : null,
  "userInfo" : {
    "userId" : 1,
    "nickname" : "nickname",
    "grade" : "BRONZE"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "fileName",
    "remotePath" : "remotePath"
  },
  "comments" : [ {
    "commentId" : 1,
    "articleId" : 1,
    "answerId" : null,
    "content" : "comment 입니다.",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
    },
    "createdAt" : "2022-12-04T00:02:53.8967092",
    "lastModifiedAt" : "2022-12-04T00:02:53.8967092"
  } ]
}
```

| Path                           | Type      | Description                    |
| ------------------------------ | --------- | ------------------------------ |
| `articleId`                    | `Number`  | 게시글의 아이디입니다.                   |
| `category`                     | `String`  | 게시글의 카테고리입니다.                  |
| `title`                        | `String`  | 게시글의 제목입니다.                    |
| `content`                      | `String`  | 게시글의 내용입니.                     |
| `clicks`                       | `Number`  | 게시글의 조회수 입니다.                  |
| `likes`                        | `Number`  | 게시글의 좋아요 숫자입니다.                |
| `isLiked`                      | `Boolean` | jwt의 회원이 좋아요를 누르면 true를 반환합니다. |
| `isBookmarked`                 | `Boolean` | jwt의 회원이 북마크 했다면 true를 반환합니다.  |
| `isClosed`                     | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.      |
| `createdAt`                    | `String`  | 게시글이 생성된 날짜입니다.                |
| `lastModifiedAt`               | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.         |
| `expiredDate`                  | `Null`    | 게시글이 유효기한입니다. 아직은 사용하지 않습니다.   |
| `tags[].tagId`                 | `Number`  | 태그 아이디 입니다.                    |
| `tags[].name`                  | `String`  | 태그 이름입니다.                      |
| `userInfo.userId`              | `Number`  | 유저의 아이디입니다.                    |
| `userInfo.nickname`            | `String`  | 유저의 닉네임입니다.                    |
| `userInfo.grade`               | `String`  | 유저의 등급입니다.                     |
| `avatar.avatarId`              | `Number`  | 아바타 파일의 아이디 입니다.               |
| `avatar.filename`              | `String`  | 아바타 파일의 이름입니다.                 |
| `avatar.remotePath`            | `String`  | 아바타 파일의 경로입니다.                 |
| `comments[].commentId`         | `Number`  | 댓글의 아이디 입니다.                   |
| `comments[].articleId`         | `Number`  | 댓글이 올라가있는 게시글의 아이디 입니다.        |
| `comments[].answerId`          | `Null`    | 게시글의 댓글이므로 답변글 필드는 null입니다.    |
| `comments[].content`           | `String`  | 댓글의 내용입니다.                     |
| `comments[].createdAt`         | `String`  | 댓글이 작성된 날짜 입니다.                |
| `comments[].lastModifiedAt`    | `String`  | 댓글이 마지막으로 수정된 날짜 입니다.          |
| `comments[].userInfo.userId`   | `Number`  | 댓글 유저의 아이디입니다.                 |
| `comments[].userInfo.nickname` | `String`  | 댓글 유저의 닉네임입니다.                 |
| `comments[].userInfo.grade`    | `String`  | 댓글 유저의 등급입니다.                  |
| `comments[].avatar.avatarId`   | `Number`  | 댓글 유저의 아바타 파일의 아이디 입니다.        |
| `comments[].avatar.filename`   | `String`  | 댓글 유저의 아바타 파일의 이름입니다.          |
| `comments[].avatar.remotePath` | `String`  | 댓글 유저의 아바타 파일의 경로입니다.          |

#### 4.2. 성공 로그인하지않은 회원이 게시글을 상세 조회시 200 <a href="#_-_-_-_-_-_-_200" id="_-_-_-_-_-_-_200"></a>

http-request

```
GET /articles/1 HTTP/1.1
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
Content-Length: 1173

{
  "articleId" : 1,
  "category" : "INFO",
  "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
  "content" : "콘탠트입니다. 제발 됬으면 좋겠습니다.",
  "clicks" : 10,
  "likes" : 1,
  "isClosed" : false,
  "isLiked" : false,
  "isBookmarked" : false,
  "tags" : [ {
    "tagId" : 1,
    "name" : "JAVA"
  } ],
  "createdAt" : "2022-12-04T00:02:54.8183213",
  "lastModifiedAt" : "2022-12-04T00:02:54.8183213",
  "expiredDate" : null,
  "userInfo" : {
    "userId" : 1,
    "nickname" : "nickname",
    "grade" : "BRONZE"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "fileName",
    "remotePath" : "remotePath"
  },
  "comments" : [ {
    "commentId" : 1,
    "articleId" : 1,
    "answerId" : null,
    "content" : "comment 입니다.",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
    },
    "createdAt" : "2022-12-04T00:02:54.8183213",
    "lastModifiedAt" : "2022-12-04T00:02:54.8183213"
  } ]
}
```

| Path                           | Type      | Description                    |
| ------------------------------ | --------- | ------------------------------ |
| `articleId`                    | `Number`  | 게시글의 아이디입니다.                   |
| `category`                     | `String`  | 게시글의 카테고리입니다.                  |
| `title`                        | `String`  | 게시글의 제목입니다.                    |
| `content`                      | `String`  | 게시글의 내용입니.                     |
| `clicks`                       | `Number`  | 게시글의 조회수 입니다.                  |
| `likes`                        | `Number`  | 게시글의 좋아요 숫자입니다.                |
| `isLiked`                      | `Boolean` | jwt의 회원이 좋아요를 누르면 true를 반환합니다. |
| `isBookmarked`                 | `Boolean` | jwt의 회원이 북마크 했다면 true를 반환합니다.  |
| `isClosed`                     | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.      |
| `createdAt`                    | `String`  | 게시글이 생성된 날짜입니다.                |
| `lastModifiedAt`               | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.         |
| `expiredDate`                  | `Null`    | 게시글이 유효기한입니다. 아직은 사용하지 않습니다.   |
| `tags[].tagId`                 | `Number`  | 태그 아이디 입니다.                    |
| `tags[].name`                  | `String`  | 태그 이름입니다.                      |
| `userInfo.userId`              | `Number`  | 유저의 아이디입니다.                    |
| `userInfo.nickname`            | `String`  | 유저의 닉네임입니다.                    |
| `userInfo.grade`               | `String`  | 유저의 등급입니다.                     |
| `avatar.avatarId`              | `Number`  | 아바타 파일의 아이디 입니다.               |
| `avatar.filename`              | `String`  | 아바타 파일의 이름입니다.                 |
| `avatar.remotePath`            | `String`  | 아바타 파일의 경로입니다.                 |
| `comments[].commentId`         | `Number`  | 댓글의 아이디 입니다..                  |
| `comments[].articleId`         | `Number`  | 댓글이 올라가있는 게시글의 아이디 입니다..       |
| `comments[].answerId`          | `Null`    | 답변글 필드는 비어있어야 합니다.             |
| `comments[].content`           | `String`  | 댓글의 내용입니다.                     |
| `comments[].createdAt`         | `String`  | 댓글이 작성된 날짜 입니다.                |
| `comments[].lastModifiedAt`    | `String`  | 댓글이 마지막으로 수정된 날짜 입니다.          |
| `comments[].userInfo.userId`   | `Number`  | 댓글 유저의 아이디입니다.                 |
| `comments[].userInfo.nickname` | `String`  | 댓글 유저의 닉네임입니다.                 |
| `comments[].userInfo.grade`    | `String`  | 댓글 유저의 등급입니다.                  |
| `comments[].avatar.avatarId`   | `Number`  | 댓글 유저의 아바타 파일의 아이디 입니다.        |
| `comments[].avatar.filename`   | `String`  | 댓글 유저의 아바타 파일의 이름입니다.          |
| `comments[].avatar.remotePath` | `String`  | 댓글 유저의 아바타 파일의 경로입니다.          |

#### 4.3. 성공 신고를 5번 이상 받은 게시글 상세 조회시 200 <a href="#_-_-_5-_-_-_-_-_-_200" id="_-_-_5-_-_-_-_-_-_200"></a>

http-request

```
GET /articles/1 HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description  |
| ------------ | ------------ |
| `article-id` | 게시글 아이디 입니다. |

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
Content-Length: 696

{
  "articleId" : 1,
  "category" : "INFO",
  "title" : "이 글은 신고가 누적되 더이상 확인하실 수 없습니다.",
  "content" : "이 글은 신고가 누적되 더이상 확인하실 수 없습니다.",
  "clicks" : 10,
  "likes" : 1,
  "isClosed" : false,
  "isLiked" : true,
  "isBookmarked" : true,
  "tags" : [ ],
  "createdAt" : "2022-12-04T00:02:56.5911379",
  "lastModifiedAt" : "2022-12-04T00:02:56.5911379",
  "expiredDate" : null,
  "userInfo" : {
    "userId" : 1,
    "nickname" : "nickname",
    "grade" : "BRONZE"
  },
  "avatar" : {
    "avatarId" : 1,
    "filename" : "fileName",
    "remotePath" : "remotePath"
  },
  "comments" : [ ]
}
```

| Path                | Type      | Description                    |
| ------------------- | --------- | ------------------------------ |
| `articleId`         | `Number`  | 게시글의 아이디입니다.                   |
| `category`          | `String`  | 게시글의 카테고리입니다.                  |
| `title`             | `String`  | 게시글의 제목입니다.                    |
| `content`           | `String`  | 게시글의 내용입니.                     |
| `clicks`            | `Number`  | 게시글의 조회수 입니다.                  |
| `likes`             | `Number`  | 게시글의 좋아요 숫자입니다.                |
| `isLiked`           | `Boolean` | jwt의 회원이 좋아요를 누르면 true를 반환합니다. |
| `isBookmarked`      | `Boolean` | jwt의 회원이 북마크 했다면 true를 반환합니다.  |
| `isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.      |
| `createdAt`         | `String`  | 게시글이 생성된 날짜입니다.                |
| `lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.         |
| `expiredDate`       | `Null`    | 게시글이 유효기한입니다. 아직은 사용하지 않습니다.   |
| `tags[]`            | `Array`   | 신고글의 태그는 빈 배열을 리턴합니다.          |
| `userInfo.userId`   | `Number`  | 유저의 아이디입니다.                    |
| `userInfo.nickname` | `String`  | 유저의 닉네임입니다.                    |
| `userInfo.grade`    | `String`  | 유저의 등급입니다.                     |
| `avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.               |
| `avatar.filename`   | `String`  | 아바타 파일의 이름입니다.                 |
| `avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.                 |
| `comments[]`        | `Array`   | 신고글의 댓글은 빈 배열을 리턴합니다.          |

#### 4.4. 실패 존재하지 않는 게시글을 상세조회시 404 <a href="#_-_-_-_-_-_404" id="_-_-_-_-_-_404"></a>

http-request

```
GET /articles/500 HTTP/1.1
Host: localhost:8080
```

| Parameter    | Description |
| ------------ | ----------- |
| `article-id` | 게시글 아이디입니다. |

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
