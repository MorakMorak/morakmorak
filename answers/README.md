# 답변(Answers)

### 1. 답변 등록 <a href="#_-_" id="_-_"></a>

#### 1.1. 답변 등록 성공\_201 <a href="#_-_" id="_-_"></a>

http-request

```
POST /articles/1/answers HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 142
Host: localhost:8080

{
  "content" : "아무말이나 적어야지~3 15글자 이상",
  "fileIdList" : [ {
    "fileId" : 1
  }, {
    "fileId" : 2
  } ]
}
```

| Path                  | Type     | Description     |
| --------------------- | -------- | --------------- |
| `content`             | `String` | 답변 본문입니다.       |
| `fileIdList[].fileId` | `Number` | 첨부파일 식별자 목록입니다. |

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
X-Frame-Options: DENY
Content-Length: 1211

{
  "data" : [ {
    "answerId" : 1,
    "content" : "contentcontentcontentcontentcontent",
    "isPicked" : true,
    "answerLikeCount" : 3,
    "commentCount" : 10,
    "createdAt" : "2022-12-04T00:02:32.1309769",
    "isLiked" : false,
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
    "commentPreview" : {
      "commentId" : 1,
      "articleId" : null,
      "answerId" : 1,
      "content" : "멋진 코딩실력을 가졌군요! 부럽다!",
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
      "createdAt" : "2022-12-04T00:02:32.1309769",
      "lastModifiedAt" : "2022-12-04T00:02:32.1309769"
    }
  } ],
  "pageInfo" : {
    "page" : 1,
    "size" : 1,
    "totalElements" : 1,
    "totalPages" : 1,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                                      | Type      | Description                         |
| ----------------------------------------- | --------- | ----------------------------------- |
| `data[]`                                  | `Array`   | 답변을 리스트 형태로 보여줍니다.                  |
| `data[].answerId`                         | `Number`  | 답변의 아이디입니다.                         |
| `data[].content`                          | `String`  | 답변 내용입니다.                           |
| `data[].answerLikeCount`                  | `Number`  | 답변의 좋아요수입니다.                        |
| `data[].isPicked`                         | `Boolean` | 답변이 채택 되었다면 true를 반환합니다.            |
| `data[].isLiked`                          | `Boolean` | 유저가 좋아요한 답변이라면 true를 반환합니다.         |
| `data[].commentCount`                     | `Number`  | 답변의 댓글 갯수입니다.                       |
| `data[].commentPreview.commentId`         | `Number`  | 답변의 댓글 식별자입니다.                      |
| `data[].commentPreview.answerId`          | `Number`  | 답변의 댓글이 소속된 답변입니다.                  |
| `data[].commentPreview.articleId`         | `Null`    | 답변 댓글이므로 게시글 식별자는 비어있습니다.           |
| `data[].commentPreview.content`           | `String`  | 답변의 댓글 내용입니다.                       |
| `data[].commentPreview.userInfo.userId`   | `Number`  | 답변의 댓글 작성자 아이디입니다.                  |
| `data[].commentPreview.userInfo.nickname` | `String`  | 답변의 댓글 작성자 닉네임입니다.                  |
| `data[].commentPreview.userInfo.grade`    | `String`  | 답변의 댓글 작성자 등급입니다.                   |
| `data[].commentPreview.avatar.avatarId`   | `Number`  | 답변의 댓글 작성자 프로필파일의 아이디 입니다.          |
| `data[].commentPreview.avatar.filename`   | `String`  | 답변의 댓글 작성자 프로필 파일의 이름입니다.           |
| `data[].commentPreview.avatar.remotePath` | `String`  | 답변의 댓글 작성자 프로필 파일의 경로입니다.           |
| `data[].commentPreview.createdAt`         | `String`  | 답변의 댓글 생성일입니다.                      |
| `data[].commentPreview.lastModifiedAt`    | `String`  | 답변의 댓글 마지막 수정일입니다.                  |
| `data[].createdAt`                        | `String`  | 답변이 생성된 날짜입니다.                      |
| `data[].userInfo.userId`                  | `Number`  | 유저의 아이디입니다.                         |
| `data[].userInfo.nickname`                | `String`  | 유저의 닉네임입니다.                         |
| `data[].userInfo.grade`                   | `String`  | 유저의 등급입니다.                          |
| `data[].avatar.avatarId`                  | `Number`  | 아바타 파일의 아이디 입니다.                    |
| `data[].avatar.filename`                  | `String`  | 아바타 파일의 이름입니다.                      |
| `data[].avatar.remotePath`                | `String`  | 아바타 파일의 경로입니다.                      |
| `pageInfo.page`                           | `Number`  | 현재 보여질 페이지 입니다.                     |
| `pageInfo.size`                           | `Number`  | 한페이지에 들어갈 답변의 갯수 입니다. 기본 설정상 5개입니다. |
| `pageInfo.totalElements`                  | `Number`  | 전체 답변의 갯수 입니다.                      |
| `pageInfo.totalPages`                     | `Number`  | 전체 페이지 숫자입니다.                       |
| `pageInfo.sort.empty`                     | `Boolean` | 페이지가 비여있다면 true를 반환합니다.             |
| `pageInfo.sort.unsorted`                  | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다.         |
| `pageInfo.sort.sorted`                    | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.            |

#### 1.2. 답변등록실패\_잘못된 카테고리\_409 <a href="#_-_-_-_409" id="_-_-_-_409"></a>

http-request

```
POST /articles/1/answers/ HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 135
Host: localhost:8080

{
  "content" : "유효한 길이의 게시물입니다.",
  "fileIdList" : [ {
    "fileId" : 1
  }, {
    "fileId" : 2
  } ]
}
```

| Path                  | Type     | Description     |
| --------------------- | -------- | --------------- |
| `content`             | `String` | 답변 본문입니다.       |
| `fileIdList[].fileId` | `Number` | 첨부파일 식별자 목록입니다. |

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
Content-Length: 138

{
  "status" : 409,
  "code" : "UNABLE_TO_ANSWER",
  "message" : "unable to post answer, article is removed",
  "validation" : null
}
```

***

### 2. 답변 수정 <a href="#_-_" id="_-_"></a>

#### 2.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

http-request

```
PATCH /articles/1/answers/1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 142
Host: localhost:8080

{
  "content" : "아무말이나 적어야지~3 15글자 이상",
  "fileIdList" : [ {
    "fileId" : 1
  }, {
    "fileId" : 2
  } ]
}
```

| Path                  | Type     | Description     |
| --------------------- | -------- | --------------- |
| `content`             | `String` | 답변 본문입니다.       |
| `fileIdList[].fileId` | `Number` | 첨부파일 식별자 목록입니다. |

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
Content-Length: 1211

{
  "data" : [ {
    "answerId" : 1,
    "content" : "contentcontentcontentcontentcontent",
    "isPicked" : false,
    "answerLikeCount" : 3,
    "commentCount" : 10,
    "createdAt" : "2022-12-04T00:02:32.1309769",
    "isLiked" : true,
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
    "commentPreview" : {
      "commentId" : 1,
      "articleId" : null,
      "answerId" : 1,
      "content" : "멋진 코딩실력을 가졌군요! 부럽다!",
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
      "createdAt" : "2022-12-04T00:02:32.1309769",
      "lastModifiedAt" : "2022-12-04T00:02:32.1309769"
    }
  } ],
  "pageInfo" : {
    "page" : 1,
    "size" : 1,
    "totalElements" : 1,
    "totalPages" : 1,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                                      | Type      | Description                         |
| ----------------------------------------- | --------- | ----------------------------------- |
| `data[]`                                  | `Array`   | 답변을 리스트 형태로 보여줍니다.                  |
| `data[].answerId`                         | `Number`  | 답변의 아이디입니다.                         |
| `data[].content`                          | `String`  | 답변 내용입니다.                           |
| `data[].answerLikeCount`                  | `Number`  | 답변의 좋아요수입니다.                        |
| `data[].isPicked`                         | `Boolean` | 답변이 채택 되었다면 true를 반환합니다.            |
| `data[].isLiked`                          | `Boolean` | 유저가 좋아요한 답변이라면 true를 반환합니다.         |
| `data[].commentCount`                     | `Number`  | 답변의 댓글 갯수입니다.                       |
| `data[].commentPreview.commentId`         | `Number`  | 답변의 댓글 식별자입니다.                      |
| `data[].commentPreview.answerId`          | `Number`  | 답변의 댓글이 소속된 답변입니다.                  |
| `data[].commentPreview.articleId`         | `Null`    | 답변 댓글이므로 게시글 식별자는 비어있습니다.           |
| `data[].commentPreview.content`           | `String`  | 답변의 댓글 내용입니다.                       |
| `data[].commentPreview.userInfo.userId`   | `Number`  | 답변의 댓글 작성자 아이디입니다.                  |
| `data[].commentPreview.userInfo.nickname` | `String`  | 답변의 댓글 작성자 닉네임입니다.                  |
| `data[].commentPreview.userInfo.grade`    | `String`  | 답변의 댓글 작성자 등급입니다.                   |
| `data[].commentPreview.avatar.avatarId`   | `Number`  | 답변의 댓글 작성자 프로필파일의 아이디 입니다.          |
| `data[].commentPreview.avatar.filename`   | `String`  | 답변의 댓글 작성자 프로필 파일의 이름입니다.           |
| `data[].commentPreview.avatar.remotePath` | `String`  | 답변의 댓글 작성자 프로필 파일의 경로입니다.           |
| `data[].commentPreview.createdAt`         | `String`  | 답변의 댓글 생성일입니다.                      |
| `data[].commentPreview.lastModifiedAt`    | `String`  | 답변의 댓글 마지막 수정일입니다.                  |
| `data[].createdAt`                        | `String`  | 답변이 생성된 날짜입니다.                      |
| `data[].userInfo.userId`                  | `Number`  | 유저의 아이디입니다.                         |
| `data[].userInfo.nickname`                | `String`  | 유저의 닉네임입니다.                         |
| `data[].userInfo.grade`                   | `String`  | 유저의 등급입니다.                          |
| `data[].avatar.avatarId`                  | `Number`  | 아바타 파일의 아이디 입니다.                    |
| `data[].avatar.filename`                  | `String`  | 아바타 파일의 이름입니다.                      |
| `data[].avatar.remotePath`                | `String`  | 아바타 파일의 경로입니다.                      |
| `pageInfo.page`                           | `Number`  | 현재 보여질 페이지 입니다.                     |
| `pageInfo.size`                           | `Number`  | 한페이지에 들어갈 답변의 갯수 입니다. 기본 설정상 5개입니다. |
| `pageInfo.totalElements`                  | `Number`  | 전체 답변의 갯수 입니다.                      |
| `pageInfo.totalPages`                     | `Number`  | 전체 페이지 숫자입니다.                       |
| `pageInfo.sort.empty`                     | `Boolean` | 페이지가 비여있다면 true를 반환합니다.             |
| `pageInfo.sort.unsorted`                  | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다.         |
| `pageInfo.sort.sorted`                    | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.            |

#### 2.2. 답변 수정 실패\_채택된 답변\_409 <a href="#_-_-_-_-_-_409" id="_-_-_-_-_-_409"></a>

http-request

```
PATCH /articles/1/answers/1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 160
Host: localhost:8080

{
  "content" : "유효한 길이의 게시물입니다.15자 이상이랍니다.",
  "fileIdList" : [ {
    "fileId" : 1
  }, {
    "fileId" : 2
  } ]
}
```

| Path                  | Type     | Description     |
| --------------------- | -------- | --------------- |
| `content`             | `String` | 답변 본문입니다.       |
| `fileIdList[].fileId` | `Number` | 첨부파일 식별자 목록입니다. |

***

### 3. 답변 조회 <a href="#_-_" id="_-_"></a>

#### 3.1. 비회원\_답변 조회 성공\_200 <a href="#_-_-_-_-_200" id="_-_-_-_-_200"></a>

http-request

```
GET /articles/1/answers?page=1&size=5 HTTP/1.1
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
Content-Length: 1211

{
  "data" : [ {
    "answerId" : 1,
    "content" : "contentcontentcontentcontentcontent",
    "isPicked" : false,
    "answerLikeCount" : 3,
    "commentCount" : 10,
    "createdAt" : "2022-12-04T00:02:32.1309769",
    "isLiked" : true,
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
    "commentPreview" : {
      "commentId" : 1,
      "articleId" : null,
      "answerId" : 1,
      "content" : "멋진 코딩실력을 가졌군요! 부럽다!",
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
      "createdAt" : "2022-12-04T00:02:32.1309769",
      "lastModifiedAt" : "2022-12-04T00:02:32.1309769"
    }
  } ],
  "pageInfo" : {
    "page" : 1,
    "size" : 5,
    "totalElements" : 1,
    "totalPages" : 1,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                                      | Type      | Description                         |
| ----------------------------------------- | --------- | ----------------------------------- |
| `data[]`                                  | `Array`   | 답변을 리스트 형태로 보여줍니다.                  |
| `data[].answerId`                         | `Number`  | 답변의 아이디입니다.                         |
| `data[].content`                          | `String`  | 답변 내용입니다.                           |
| `data[].answerLikeCount`                  | `Number`  | 답변의 좋아요수입니다.                        |
| `data[].isPicked`                         | `Boolean` | 답변이 채택 되었다면 true를 반환합니다.            |
| `data[].isLiked`                          | `Boolean` | 비로그인 유저에게는 좋아요가 false로 반환됩니다.       |
| `data[].commentCount`                     | `Number`  | 답변의 댓글 갯수입니다.                       |
| `data[].commentPreview.commentId`         | `Number`  | 답변의 댓글 식별자입니다.                      |
| `data[].commentPreview.answerId`          | `Number`  | 답변의 댓글이 소속된 답변입니다.                  |
| `data[].commentPreview.articleId`         | `Null`    | 답변 댓글이므로 게시글 식별자는 비어있습니다.           |
| `data[].commentPreview.content`           | `String`  | 답변의 댓글 내용입니다.                       |
| `data[].commentPreview.userInfo.userId`   | `Number`  | 답변의 댓글 작성자 아이디입니다.                  |
| `data[].commentPreview.userInfo.nickname` | `String`  | 답변의 댓글 작성자 닉네임입니다.                  |
| `data[].commentPreview.userInfo.grade`    | `String`  | 답변의 댓글 작성자 등급입니다.                   |
| `data[].commentPreview.avatar.avatarId`   | `Number`  | 답변의 댓글 작성자 프로필파일의 아이디 입니다.          |
| `data[].commentPreview.avatar.filename`   | `String`  | 답변의 댓글 작성자 프로필 파일의 이름입니다.           |
| `data[].commentPreview.avatar.remotePath` | `String`  | 답변의 댓글 작성자 프로필 파일의 경로입니다.           |
| `data[].commentPreview.createdAt`         | `String`  | 답변의 댓글 생성일입니다.                      |
| `data[].commentPreview.lastModifiedAt`    | `String`  | 답변의 댓글 마지막 수정일입니다.                  |
| `data[].createdAt`                        | `String`  | 답변이 생성된 날짜입니다.                      |
| `data[].userInfo.userId`                  | `Number`  | 유저의 아이디입니다.                         |
| `data[].userInfo.nickname`                | `String`  | 유저의 닉네임입니다.                         |
| `data[].userInfo.grade`                   | `String`  | 유저의 등급입니다.                          |
| `data[].avatar.avatarId`                  | `Number`  | 아바타 파일의 아이디 입니다.                    |
| `data[].avatar.filename`                  | `String`  | 아바타 파일의 이름입니다.                      |
| `data[].avatar.remotePath`                | `String`  | 아바타 파일의 경로입니다.                      |
| `pageInfo.page`                           | `Number`  | 현재 보여질 페이지 입니다.                     |
| `pageInfo.size`                           | `Number`  | 한페이지에 들어갈 답변의 갯수 입니다. 기본 설정상 5개입니다. |
| `pageInfo.totalElements`                  | `Number`  | 전체 답변의 갯수 입니다.                      |
| `pageInfo.totalPages`                     | `Number`  | 전체 페이지 숫자입니다.                       |
| `pageInfo.sort.empty`                     | `Boolean` | 페이지가 비여있다면 true를 반환합니다.             |
| `pageInfo.sort.unsorted`                  | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다.         |
| `pageInfo.sort.sorted`                    | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.            |

#### 3.2. 회원\_답변 조회 성공\_200 <a href="#_-_-_-_-_200" id="_-_-_-_-_200"></a>

http-request

```
GET /articles/1/answers?page=1&size=5 HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description  |
| ------------ | ------------ |
| `article-id` | 게시글의 아이디입니다. |

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
Content-Length: 2229

{
  "data" : [ {
    "answerId" : 1,
    "content" : "좋아요 표시한 답변",
    "isPicked" : false,
    "answerLikeCount" : 3,
    "commentCount" : 10,
    "createdAt" : "2022-12-04T00:02:32.1309769",
    "isLiked" : false,
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
    "commentPreview" : {
      "commentId" : 1,
      "articleId" : null,
      "answerId" : 1,
      "content" : "멋진 코딩실력을 가졌군요! 부럽다!",
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
      "createdAt" : "2022-12-04T00:02:32.1309769",
      "lastModifiedAt" : "2022-12-04T00:02:32.1309769"
    }
  }, {
    "answerId" : 2,
    "content" : "유저가 좋아요를 누르지 않은 답변입니다.",
    "isPicked" : false,
    "answerLikeCount" : 3,
    "commentCount" : 10,
    "createdAt" : "2022-12-04T00:02:32.1309769",
    "isLiked" : true,
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
    "commentPreview" : {
      "commentId" : 2,
      "articleId" : null,
      "answerId" : 1,
      "content" : "김코딩코딩씨 모락모락 구운감자가 되어주세요.",
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
      "createdAt" : "2022-12-04T00:02:32.1309769",
      "lastModifiedAt" : "2022-12-04T00:02:32.1309769"
    }
  } ],
  "pageInfo" : {
    "page" : 1,
    "size" : 5,
    "totalElements" : 1,
    "totalPages" : 1,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                                      | Type      | Description                         |
| ----------------------------------------- | --------- | ----------------------------------- |
| `data[]`                                  | `Array`   | 답변을 리스트 형태로 보여줍니다.                  |
| `data[].answerId`                         | `Number`  | 답변의 아이디입니다.                         |
| `data[].content`                          | `String`  | 답변 내용입니다.                           |
| `data[].answerLikeCount`                  | `Number`  | 답변의 좋아요수입니다.                        |
| `data[].isPicked`                         | `Boolean` | 답변이 채택 되었다면 true를 반환합니다.            |
| `data[].isLiked`                          | `Boolean` | 유저가 좋아요를 눌렀다면 true를 반환합니다.          |
| `data[].commentCount`                     | `Number`  | 답변의 댓글 갯수입니다.                       |
| `data[].commentPreview.commentId`         | `Number`  | 답변의 댓글 식별자입니다.                      |
| `data[].commentPreview.answerId`          | `Number`  | 답변의 댓글이 소속된 답변입니다.                  |
| `data[].commentPreview.articleId`         | `Null`    | 답변 댓글이므로 게시글 식별자는 비어있습니다.           |
| `data[].commentPreview.content`           | `String`  | 답변의 댓글 내용입니다.                       |
| `data[].commentPreview.userInfo.userId`   | `Number`  | 답변의 댓글 작성자 아이디입니다.                  |
| `data[].commentPreview.userInfo.nickname` | `String`  | 답변의 댓글 작성자 닉네임입니다.                  |
| `data[].commentPreview.userInfo.grade`    | `String`  | 답변의 댓글 작성자 등급입니다.                   |
| `data[].commentPreview.avatar.avatarId`   | `Number`  | 답변의 댓글 작성자 프로필파일의 아이디 입니다.          |
| `data[].commentPreview.avatar.filename`   | `String`  | 답변의 댓글 작성자 프로필 파일의 이름입니다.           |
| `data[].commentPreview.avatar.remotePath` | `String`  | 답변의 댓글 작성자 프로필 파일의 경로입니다.           |
| `data[].commentPreview.createdAt`         | `String`  | 답변의 댓글 생성일입니다.                      |
| `data[].commentPreview.lastModifiedAt`    | `String`  | 답변의 댓글 마지막 수정일입니다.                  |
| `data[].createdAt`                        | `String`  | 답변이 생성된 날짜입니다.                      |
| `data[].userInfo.userId`                  | `Number`  | 유저의 아이디입니다.                         |
| `data[].userInfo.nickname`                | `String`  | 유저의 닉네임입니다.                         |
| `data[].userInfo.grade`                   | `String`  | 유저의 등급입니다.                          |
| `data[].avatar.avatarId`                  | `Number`  | 아바타 파일의 아이디 입니다.                    |
| `data[].avatar.filename`                  | `String`  | 아바타 파일의 이름입니다.                      |
| `data[].avatar.remotePath`                | `String`  | 아바타 파일의 경로입니다.                      |
| `pageInfo.page`                           | `Number`  | 현재 보여질 페이지 입니다.                     |
| `pageInfo.size`                           | `Number`  | 한페이지에 들어갈 답변의 갯수 입니다. 기본 설정상 5개입니다. |
| `pageInfo.totalElements`                  | `Number`  | 전체 답변의 갯수 입니다.                      |
| `pageInfo.totalPages`                     | `Number`  | 전체 페이지 숫자입니다.                       |
| `pageInfo.sort.empty`                     | `Boolean` | 페이지가 비여있다면 true를 반환합니다.             |
| `pageInfo.sort.unsorted`                  | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다.         |
| `pageInfo.sort.sorted`                    | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.            |

#### 3.3. 유저 대시보드 답변목록 조회 성공\_200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /users/1/answers?page=1&size=50 HTTP/1.1
Host: localhost:8080
```

| Parameter | Description    |
| --------- | -------------- |
| `user-id` | 유효한 형식의 유저 아이디 |

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
Content-Length: 959

{
  "data" : [ {
    "articleId" : 1,
    "answerId" : 1,
    "content" : "픽미픽미픽미업 채택된 짱 멋진 답변입니다 후후후!",
    "isPicked" : true,
    "answerLikeCount" : 3,
    "commentCount" : 10,
    "createdAt" : "2022-12-04T00:02:32.1309769",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    }
  }, {
    "articleId" : 2,
    "answerId" : 2,
    "content" : "채택되지 못한 답변입니다. 다음 기회에~",
    "isPicked" : false,
    "answerLikeCount" : 3,
    "commentCount" : 10,
    "createdAt" : "2022-12-04T00:02:32.1309769",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    }
  } ],
  "pageInfo" : {
    "page" : 1,
    "size" : 50,
    "totalElements" : 1,
    "totalPages" : 1,
    "sort" : {
      "empty" : true,
      "sorted" : false,
      "unsorted" : true
    }
  }
}
```

| Path                       | Type      | Description                         |
| -------------------------- | --------- | ----------------------------------- |
| `data[]`                   | `Array`   | 답변을 리스트 형태로 보여줍니다.                  |
| `data[].articleId`         | `Number`  | 답변이 속한 게시글의 아이디입니다.                 |
| `data[].answerId`          | `Number`  | 답변의 아이디입니다.                         |
| `data[].isPicked`          | `Boolean` | 답변이 채택 되었다면 true를 반환합니다.            |
| `data[].content`           | `String`  | 답변 내용입니다.                           |
| `data[].answerLikeCount`   | `Number`  | 답변의 좋아요수입니다.                        |
| `data[].commentCount`      | `Number`  | 답변의 댓글 갯수입니다.                       |
| `data[].createdAt`         | `String`  | 답변이 생성된 날짜입니다.                      |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                         |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                         |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                          |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.                     |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 답변의 갯수 입니다. 기본 설정상 5개입니다. |
| `pageInfo.totalElements`   | `Number`  | 전체 답변의 갯수 입니다.                      |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.                       |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.             |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다.         |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.            |

#### 3.4. 유저 답변목록\_조회\_실패\_404 <a href="#_-_-_-_-_404" id="_-_-_-_-_404"></a>

http-request

```
GET /users/1/answers?page=1&size=50 HTTP/1.1
Host: docs.api.com
```

| Parameter | Description                   |
| --------- | ----------------------------- |
| `user-id` | 존재하지 않는 유저의 아이디 혹은 잘못된 아이디 형식 |

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

### 4. 답변 좋아요 <a href="#_-_" id="_-_"></a>

#### 4.1. 답변\_좋아요\_처음누를때\_성공\_200 <a href="#_-_-_-_-_200" id="_-_-_-_-_200"></a>

http-request

```
POST /articles/1/answers/1/likes HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |
| `answer-id`  | 답변글의 아이디 입니다. |

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
Content-Length: 80

{
  "answerId" : 1,
  "userId" : 1,
  "isLiked" : true,
  "likeCount" : 1
}
```

| Path        | Type      | Description                   |
| ----------- | --------- | ----------------------------- |
| `answerId`  | `Number`  | 답변글의 아이디 입니다.                 |
| `userId`    | `Number`  | 유저의 아이디 입니다.                  |
| `isLiked`   | `Boolean` | 해당 유저가 좋아요를 눌렀는지 안눌렀지를 보여줍니다, |
| `likeCount` | `Number`  | 해당 게시글의 좋아요 숫자입니다.            |

#### 4.2. 답변글\_좋아요\_두번\_누를때\_취소\_성공\_200 <a href="#_-_-_-_-_-_-_200" id="_-_-_-_-_-_-_200"></a>

http-request

```
POST /articles/1/answers/1/likes HTTP/1.1
Authorization: AccessToken
Host: localhost:8080
```

| Parameter    | Description   |
| ------------ | ------------- |
| `article-id` | 게시글의 아이디 입니다. |
| `answer-id`  | 답변글의 아이디 입니다. |

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
Content-Length: 80

{
  "answerId" : 1,
  "userId" : 1,
  "isLiked" : true,
  "likeCount" : 0
}
```

| Path        | Type      | Description                   |
| ----------- | --------- | ----------------------------- |
| `answerId`  | `Number`  | 답변글의 아이디 입니다.                 |
| `userId`    | `Number`  | 유저의 아이디 입니다.                  |
| `isLiked`   | `Boolean` | 해당 유저가 좋아요를 눌렀는지 안눌렀지를 보여줍니다, |
| `likeCount` | `Number`  | 해당 게시글의 좋아요 숫자입니다.            |

Last updated 2022-12-04 03:30:05 +0900
