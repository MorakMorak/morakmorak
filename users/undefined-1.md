# 알림 기능

### 1. 유저 알림 조회 <a href="#_-_-_" id="_-_-_"></a>

#### 1.1. 유저 알림 리스트 조회\_성공200 <a href="#_-_-_-_-_-200" id="_-_-_-_-_-200"></a>

http-request

```
GET /notifications?page=1&size=10 HTTP/1.1
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc4OSwiZXhwIjoxNjcwMDgxNTg5fQ.Nwz5VglL4Vnqq87lK2wJ7nppVBG1rjTW7IX2OpqXY3E
Host: docs.api.com
```

| Parameter | Description |
| --------- | ----------- |
| `page`    | 현재 페이지      |
| `size`    | 현재 사이즈      |

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
Content-Length: 686

{
  "data" : [ {
    "notificationId" : 1,
    "message" : "회원님이 작성하신 \"자바 2명 타세요\" 게시글이 좋아요 10개 돌파했습니다.",
    "isChecked" : false,
    "createdAt" : "2022-12-04T00:03:09.3395894"
  }, {
    "notificationId" : 2,
    "message" : "회원님이 작성하신 \"자바 2명 타세요\" 게시글이 좋아요 10개 돌파했습니다.",
    "isChecked" : false,
    "createdAt" : "2022-12-04T00:03:09.3395894"
  } ],
  "pageInfo" : {
    "page" : 2,
    "size" : 10,
    "totalElements" : 12,
    "totalPages" : 2,
    "sort" : {
      "empty" : true,
      "sorted" : false,
      "unsorted" : true
    }
  }
}
```

| Path                     | Type      | Description           |
| ------------------------ | --------- | --------------------- |
| `data[].notificationId`  | `Number`  | 알림 id                 |
| `data[].message`         | `String`  | 알림 메세지                |
| `data[].isChecked`       | `Boolean` | 유저가 해당 메세지를 확인(클릭)했는지 |
| `data[].createdAt`       | `String`  | 알림이 생성된 일시            |
| `pageInfo.page`          | `Number`  | 현재 페이지                |
| `pageInfo.size`          | `Number`  | 페이즈당 사이즈              |
| `pageInfo.totalElements` | `Number`  | 전체 객체 수               |
| `pageInfo.totalPages`    | `Number`  | 전체 페이지 수              |
| `pageInfo.sort.empty`    | `Boolean` | 정렬 조건이 없다면 true       |
| `pageInfo.sort.unsorted` | `Boolean` | 정렬되지 않았다면 true        |
| `pageInfo.sort.sorted`   | `Boolean` | 정렬되었다면 true           |

#### 1.2. 유저 알림 리스트 조회\_실패404 <a href="#_-_-_-_-_-404" id="_-_-_-_-_-404"></a>

http-request

```
GET /notifications?page=1&size=2 HTTP/1.1
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc4OSwiZXhwIjoxNjcwMDgxNTg5fQ.Nwz5VglL4Vnqq87lK2wJ7nppVBG1rjTW7IX2OpqXY3E
Host: docs.api.com
```

| Parameter | Description |
| --------- | ----------- |
| `page`    | 현재 페이지      |
| `size`    | 현재 사이즈      |

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

***

### 2. 유저 알림 개별 조회(클릭) <a href="#_-_-_-_" id="_-_-_-_"></a>

#### 2.1. 유저 알림 조회\_성공308 <a href="#_-_-_-_-308" id="_-_-_-_-308"></a>

http-request

```
GET /notifications/1 HTTP/1.1
Host: docs.api.com
```

http-response

```
HTTP/1.1 308 Permanent Redirect
Vary: Origin
Vary: Access-Control-Request-Method
Vary: Access-Control-Request-Headers
Location: localhost:8080.com/anyString
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
X-Frame-Options: DENY
```

***

### 3. 유저 알림 읽음 처리 <a href="#_-_-_-_2" id="_-_-_-_2"></a>

#### 3.1. 유저 알림 삭제\_성공204 <a href="#_-_-_-_-204" id="_-_-_-_-204"></a>

http-request

```
DELETE /notifications/1 HTTP/1.1
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc4OSwiZXhwIjoxNjcwMDgxNTg5fQ.Nwz5VglL4Vnqq87lK2wJ7nppVBG1rjTW7IX2OpqXY3E
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

#### 3.2. 유저 알림 삭제\_실패403 <a href="#_-_-_-_-403" id="_-_-_-_-403"></a>

http-request

```
DELETE /notifications/1 HTTP/1.1
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc4OSwiZXhwIjoxNjcwMDgxNTg5fQ.Nwz5VglL4Vnqq87lK2wJ7nppVBG1rjTW7IX2OpqXY3E
Host: docs.api.com
```

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

#### 3.3. 유저 알림 삭제\_실패404 <a href="#_-_-_-_-404" id="_-_-_-_-404"></a>

http-request

```
DELETE /notifications/1 HTTP/1.1
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyQHRlc3QuY29tIiwiaWQiOjEsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJuaWNrbmFtZSI6InRlc3RVc2VyMSIsImlhdCI6MTY3MDA3OTc4OSwiZXhwIjoxNjcwMDgxNTg5fQ.Nwz5VglL4Vnqq87lK2wJ7nppVBG1rjTW7IX2OpqXY3E
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
Content-Length: 125

{
  "status" : 404,
  "code" : "NOTIFICATION_NOT_FOUND",
  "message" : "notification not found",
  "validation" : null
}
```
