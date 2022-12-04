# 회원 랭킹(Ranks)

### 1. 유저 랭킹 조회 <a href="#_-_-_" id="_-_-_"></a>

#### 1.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

http-request

```
GET /users/ranks?size=2&page=1&q=point HTTP/1.1
Host: docs.api.com
```

| Parameter | Description                                             |
| --------- | ------------------------------------------------------- |
| `q`       | 정렬 조건 - articles(게시글 작성순), answers(답변 작성순), point(포인트순) |
| `page`    | 현재 페이지                                                  |
| `size`    | 페이지당 개수                                                 |

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
Content-Length: 1075

{
  "data" : [ {
    "userId" : 1,
    "nickname" : "testUser2",
    "infoMessage" : "아무말이나 적어야지~",
    "point" : 1,
    "grade" : "VIP",
    "jobType" : "DEVELOPER",
    "articleCount" : 1,
    "likeCount" : 1,
    "answerCount" : 1,
    "rank" : 2,
    "avatar" : {
      "avatarId" : 1,
      "filename" : "아무말이나 적어야지~",
      "remotePath" : "아무말이나 적어야지~2"
    }
  }, {
    "userId" : 1,
    "nickname" : "testUser2",
    "infoMessage" : "아무말이나 적어야지~",
    "point" : 1,
    "grade" : "VIP",
    "jobType" : "DEVELOPER",
    "articleCount" : 1,
    "likeCount" : 1,
    "answerCount" : 1,
    "rank" : 2,
    "avatar" : {
      "avatarId" : 1,
      "filename" : "아무말이나 적어야지~",
      "remotePath" : "아무말이나 적어야지~2"
    }
  } ],
  "pageInfo" : {
    "page" : 2,
    "size" : 2,
    "totalElements" : 4,
    "totalPages" : 2,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                       | Type      | Description                            |
| -------------------------- | --------- | -------------------------------------- |
| `data[].rank`              | `Number`  | 임시로 넣어놨으며 아직 별도 구현 예정 없습니다, 필요 시 협의 필요 |
| `data[].userId`            | `Number`  | 유저 db 시퀀스값                             |
| `data[].answerCount`       | `Number`  | 답변 작성 횟수                               |
| `data[].infoMessage`       | `String`  | 자기소개                                   |
| `data[].jobType`           | `String`  | 직업                                     |
| `data[].grade`             | `String`  | 등급                                     |
| `data[].nickname`          | `String`  | 이메일                                    |
| `data[].likeCount`         | `Number`  | 받은 좋아요 수                               |
| `data[].point`             | `Number`  | 보유 포인트                                 |
| `data[].articleCount`      | `Number`  | 게시글(정보+질문)글 작성 횟수                      |
| `data[].avatar`            | `Object`  | 유저 프로필 이미지 객체                          |
| `data[].avatar.avatarId`   | `Number`  | 프로필 이미지 db 시퀀스                         |
| `data[].avatar.filename`   | `String`  | 프로필 이미지 파일명                            |
| `data[].avatar.remotePath` | `String`  | 프로필 이미지 서버 url                         |
| `pageInfo.totalElements`   | `Number`  | db 데이터 총 개수                            |
| `pageInfo.totalPages`      | `Number`  | 총 페이지 개수                               |
| `pageInfo.page`            | `Number`  | 현재 페이지                                 |
| `pageInfo.size`            | `Number`  | 페이지 사이즈                                |
| `pageInfo.sort.empty`      | `Boolean` | 해당 페이지가 비어있는지                          |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되어 있다면 true                     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true                    |
