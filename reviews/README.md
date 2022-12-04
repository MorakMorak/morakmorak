# 채택/후원(Reviews)

### 1. 답변 채택 <a href="#_-_201" id="_-_201"></a>

#### 1.1. 성공 201 <a href="#_-_201" id="_-_201"></a>

http-request

```
POST /articles/1/answers/1/reviews HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 249
Host: localhost:8080

{
  "content" : "15글자 이상의 정성스러운 답변",
  "badges" : [ {
    "badgeId" : 1,
    "name" : "HELPFUL"
  }, {
    "badgeId" : 2,
    "name" : "SMART"
  }, {
    "badgeId" : 3,
    "name" : "WISE"
  } ],
  "point" : 10
}
```

| Path               | Type     | Description       |
| ------------------ | -------- | ----------------- |
| `content`          | `String` | 15자 이상의 리뷰 내용입니다. |
| `badges[].badgeId` | `Number` | 선택한 뱃지 식별자입니다.    |
| `badges[].name`    | `String` | 선택한 뱃지의 이름입니다.    |
| `point`            | `Number` | 보내는 포인트입니다.       |

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
Content-Length: 518

{
  "reviewId" : 1,
  "articleId" : 1,
  "answerId" : 1,
  "content" : "JPA는 아무잘못이없다구요. 아시겠어요? ",
  "senderId" : 1,
  "senderNickname" : "더티체킹해주세요",
  "remainingPoint" : 50,
  "receiverId" : 2,
  "receiverNickname" : "코딩왕"김모락,
  "createdAt" : "2022-12-03T01:04:41.6167764",
  "badges" : [ {
    "badgeId" : 1,
    "name" : "HELPFUL"
  }, {
    "badgeId" : 2,
    "name" : "SMART"
  }, {
    "badgeId" : 3,
    "name" : "WISE"
  } ]
}
```

| Path               | Type     | Description     |
| ------------------ | -------- | --------------- |
| `content`          | `String` | 리뷰 내용입니다.       |
| `remainingPoint`   | `Number` | 리뷰 내용입니다.       |
| `articleId`        | `Number` | 질문글 식별자입니다.     |
| `answerId`         | `Number` | 채택된 답변 식별자입니다.  |
| `senderId`         | `Number` | 보내는 유저 아이디입니다.  |
| `senderNickname`   | `String` | 보내는 유저 닉네임입니다.  |
| `receiverId`       | `Number` | 받는 유저 아이디 입니다.  |
| `receiverNickname` | `String` | 받는 유저 닉네임입니다.   |
| `reviewId`         | `Number` | 생성된 리뷰의 식별자입니다. |
| `createdAt`        | `String` | 리뷰 등록일시입니다.     |
| `badges[].badgeId` | `Number` | 선택한 뱃지 식별자입니다.  |
| `badges[].name`    | `String` | 선택한 뱃지의 이름입니다.  |

#### 1.2. 실패 409 본인 채택 불가 <a href="#_-_409_-_-_" id="_-_409_-_-_"></a>

http-request

```
POST /articles/1/answers/1/reviews HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 250
Host: localhost:8080

{
  "content" : "15글자 이상의 정성스러운 답변",
  "badges" : [ {
    "badgeId" : 1,
    "name" : "HELPFUL"
  }, {
    "badgeId" : 2,
    "name" : "SMART"
  }, {
    "badgeId" : 3,
    "name" : "WISE"
  } ],
  "point" : 500
}
```

| Path               | Type     | Description       |
| ------------------ | -------- | ----------------- |
| `content`          | `String` | 15자 이상의 리뷰 내용입니다. |
| `badges[].badgeId` | `Number` | 선택한 뱃지 식별자입니다.    |
| `badges[].name`    | `String` | 선택한 뱃지의 이름입니다.    |
| `point`            | `Number` | 유효한 포인트입니다.       |

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
Content-Length: 170

{
  "status" : 409,
  "code" : "UNABLE_TO_REVIEW",
  "message" : "unable to post review, article is already closed or status is not posting",
  "validation" : null
}
```

#### 1.3. 실패 422 잘못된 포인트 <a href="#_-_422_-_" id="_-_422_-_"></a>

http-request

```
POST /articles/1/answers/1/reviews HTTP/1.1
Content-Type: application/json;charset=UTF-8
Authorization: AccessToken
Content-Length: 250
Host: localhost:8080

{
  "content" : "15글자 이상의 정성스러운 답변",
  "badges" : [ {
    "badgeId" : 1,
    "name" : "HELPFUL"
  }, {
    "badgeId" : 2,
    "name" : "SMART"
  }, {
    "badgeId" : 3,
    "name" : "WISE"
  } ],
  "point" : 500
}
```

| Path               | Type     | Description                    |
| ------------------ | -------- | ------------------------------ |
| `content`          | `String` | 15자 이상의 리뷰 내용입니다.              |
| `badges[].badgeId` | `Number` | 선택한 뱃지 식별자입니다.                 |
| `badges[].name`    | `String` | 선택한 뱃지의 이름입니다.                 |
| `point`            | `Number` | 보내는 포인트가 유저의 잔여포인트보다 많은 경우입니다. |

http-response

```
HTTP/1.1 422 Unprocessable Entity
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
Content-Length: 162

{
  "status" : 422,
  "code" : "UNPROCESSABLE_REQUEST",
  "message" : "contained instruction has correct syntax, but unprocessable.",
  "validation" : null
}
```

***
