# 게시글 검색

### 1.제목으로 검색 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

#### 1.1. 성공 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=info&keyword=%ED%85%8C%EC%8A%A4%ED%8A%B8+%ED%83%80%EC%9D%B4%ED%8B%80%EC%9E%85%EB%8B%88%EB%8B%A4.+%EC%9E%98%EB%B6%80%ED%83%81%EB%93%9C%EB%A6%BD%EB%8B%88%EB%8B%A4.+%EC%A0%9C%EB%B0%9C+%EB%8F%BC%EB%9D%BC%21%21%21%7E%7E%7E%7E%7E%7E%7E%7E&target=title&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:54.1517403",
    "lastModifiedAt" : "2022-12-04T00:02:54.1517403",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.2. 실패 존재하지 않는 제목으로 검색  <a href="#_-_-_-_-_-_-_-_200" id="_-_-_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=info&keyword=%EC%A1%B4%EC%9E%AC%ED%95%98%EC%A7%80+%EC%95%8A%EC%9D%8C&target=title&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 224

{
  "data" : [ ],
  "pageInfo" : {
    "page" : 1,
    "size" : 1,
    "totalElements" : 0,
    "totalPages" : 0,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                     | Type      | Description                 |
| ------------------------ | --------- | --------------------------- |
| `data[]`                 | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `pageInfo.page`          | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`          | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements` | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`    | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`    | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted` | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`   | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

### 2. 태그명으로 검색 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

#### 2.1. 성공 게시글 검색시 태그명으로 검색 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=JAVA&target=tag&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.9385357",
    "lastModifiedAt" : "2022-12-04T00:02:55.9385357",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 2.2. 실패 200 존재하지 않는 태그명 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=NO&target=tag&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 224

{
  "data" : [ ],
  "pageInfo" : {
    "page" : 1,
    "size" : 1,
    "totalElements" : 0,
    "totalPages" : 0,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                     | Type      | Description                 |
| ------------------------ | --------- | --------------------------- |
| `data[]`                 | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `pageInfo.page`          | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`          | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements` | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`    | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`    | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted` | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`   | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

### 3. 내용으로 검색 <a href="#_-_-_-_-_200" id="_-_-_-_-_200"></a>

#### 3.1 성공  200 <a href="#_-_-_-_-_200" id="_-_-_-_-_200"></a>

http-request

{% code overflow="wrap" lineNumbers="true" %}
```
GET /articles?category=INFO&keyword=%EC%BD%98%ED%83%A0%ED%8A%B8%EC%9E%85%EB%8B%88%EB%8B%A4&target=content&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```
{% endcode %}

| Parameter  | Description      |
| ---------- | ---------------- |
| `category` | 카테고리 검색          |
| `keyword`  | 검색어              |
| `target`   | 검색할 대상           |
| `sort`     | 정렬조건 기능          |
| `page`     | 현재 보여질 페이지 번호    |
| `size`     | 한페이지에 보여질 게시글 개수 |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:56.0217425",
    "lastModifiedAt" : "2022-12-04T00:02:56.0217425",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.6. 실패 존재하지 않는 게시글의 내용 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=%EC%BD%98%ED%83%A0%ED%8A%B8%EC%9E%85%EB%8B%88%EB%8B%A4&target=content&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 224

{
  "data" : [ ],
  "pageInfo" : {
    "page" : 1,
    "size" : 1,
    "totalElements" : 0,
    "totalPages" : 0,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                     | Type      | Description                 |
| ------------------------ | --------- | --------------------------- |
| `data[]`                 | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `pageInfo.page`          | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`          | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements` | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`    | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`    | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted` | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`   | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.7. 성공 게시글의 제목과 내용으로 검색 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=%ED%83%80%EC%9D%B4%ED%8B%80&target=titleAndContent&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:56.2629564",
    "lastModifiedAt" : "2022-12-04T00:02:56.2629564",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.8. 실패 존재하지 않는 게시글의 제목과 내용으로 검색 200 <a href="#_-_-_-_-_-_-_-_200" id="_-_-_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=%EC%A1%B4%EC%9E%AC%ED%95%98%EC%A7%80+%EC%95%8A%EC%9D%8C&target=titleAndContent&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 224

{
  "data" : [ ],
  "pageInfo" : {
    "page" : 1,
    "size" : 1,
    "totalElements" : 0,
    "totalPages" : 0,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                     | Type      | Description                 |
| ------------------------ | --------- | --------------------------- |
| `data[]`                 | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `pageInfo.page`          | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`          | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements` | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`    | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`    | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted` | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`   | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.9. 성공 게시글 검색시 해당 유저의 아이디로 북마크 조회 성공 200 <a href="#_-_-_-_-_-_-_-_-_-_200" id="_-_-_-_-_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=1&target=bookmark&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:56.4263234",
    "lastModifiedAt" : "2022-12-04T00:02:56.4263234",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.10. 실패 게시글 검색시 존재하지 않는 유저의 아이디 또는 북마크가 없을 경우 실패 200 <a href="#_-_-_-_-_-_-_-_-_-_-_-_-_200" id="_-_-_-_-_-_-_-_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=1&target=bookmark&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 224

{
  "data" : [ ],
  "pageInfo" : {
    "page" : 1,
    "size" : 1,
    "totalElements" : 0,
    "totalPages" : 0,
    "sort" : {
      "empty" : false,
      "sorted" : true,
      "unsorted" : false
    }
  }
}
```

| Path                     | Type      | Description                 |
| ------------------------ | --------- | --------------------------- |
| `data[]`                 | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `pageInfo.page`          | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`          | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements` | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`    | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`    | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted` | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`   | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.11. 성공 게시글검색 정렬조건 최근순 200 <a href="#_-_-_-_-_200" id="_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.1989468",
    "lastModifiedAt" : "2022-12-04T00:02:55.1989468",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.12. 성공 게시글검색 정렬조건 오래된순 200 <a href="#_-_-_-_-_200" id="_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=asc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.2677072",
    "lastModifiedAt" : "2022-12-04T00:02:55.2677072",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.13. 성공 게시글검색 정렬조건 댓글갯수 최근순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=comment-desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.4108971",
    "lastModifiedAt" : "2022-12-04T00:02:55.4108971",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.14. 성공 게시글검색 정렬조건 댓글갯수 오래된순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=comment-asc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.3398384",
    "lastModifiedAt" : "2022-12-04T00:02:55.3398384",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.15. 성공 게시글 정렬조건 좋아요수 최근순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=like-desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.4756069",
    "lastModifiedAt" : "2022-12-04T00:02:55.4756069",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.16. 성공 게시글검색 정렬조건 좋아요수 오래된순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=like-asc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.5414328",
    "lastModifiedAt" : "2022-12-04T00:02:55.5414328",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.17. 성공 게시글검색 정렬조건 답변수 최근순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=answer-desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.6080128",
    "lastModifiedAt" : "2022-12-04T00:02:55.6080128",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.18. 성공 게시글검색 정렬조건 답변수 오래된순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=answer-asc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 883

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.673341",
    "lastModifiedAt" : "2022-12-04T00:02:55.673341",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.19. 성공 게시글검색 정렬조건 채택 안된순 최근순 200 <a href="#_-_-_-_-_-_-_200" id="_-_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=isChecked-false-desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:54.9518545",
    "lastModifiedAt" : "2022-12-04T00:02:54.9518545",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.20. 성공 게시글검색 정렬조건 채택안된순 오래된순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=isChecked-false-asc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 885

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : false,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.0656811",
    "lastModifiedAt" : "2022-12-04T00:02:55.0656811",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.21. 성공 게시글검색 정렬조건 채택된순 최근순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=isChecked-true-desc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 884

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : true,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.7345614",
    "lastModifiedAt" : "2022-12-04T00:02:55.7345614",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |

#### 1.22. 성공 게시글검색 정렬조건 채택된것 오래된순 200 <a href="#_-_-_-_-_-_200" id="_-_-_-_-_-_200"></a>

http-request

```
GET /articles?category=INFO&keyword=null&target=null&sort=isChecked-true-asc&page=1&size=1 HTTP/1.1
Host: localhost:8080
```

| Parameter  | Description           |
| ---------- | --------------------- |
| `category` | 카테고리 검색 기능입니다.        |
| `keyword`  | 검색어 입니다.              |
| `target`   | 검색할 대상입니다.            |
| `sort`     | 정렬조건 기능입니다.           |
| `page`     | 현재 보여질 페이지 번호입니다.     |
| `size`     | 한페이지에 보여질 게시글의 갯수입니다. |

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
Content-Length: 884

{
  "data" : [ {
    "articleId" : 1,
    "category" : "INFO",
    "title" : "테스트 타이틀입니다. 잘부탁드립니다. 제발 돼라!!!~~~~~~~~",
    "clicks" : 10,
    "likes" : 1,
    "isClosed" : true,
    "tags" : [ {
      "tagId" : 1,
      "name" : "JAVA"
    } ],
    "commentCount" : 1,
    "answerCount" : 1,
    "createdAt" : "2022-12-04T00:02:55.8040671",
    "lastModifiedAt" : "2022-12-04T00:02:55.8040671",
    "userInfo" : {
      "userId" : 1,
      "nickname" : "nickname",
      "grade" : "BRONZE"
    },
    "avatar" : {
      "avatarId" : 1,
      "filename" : "fileName",
      "remotePath" : "remotePath"
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

| Path                       | Type      | Description                 |
| -------------------------- | --------- | --------------------------- |
| `data[]`                   | `Array`   | 게시글을 리스트 형태로 보여줍니다.         |
| `data[].articleId`         | `Number`  | 게시글의 아이디입니다.                |
| `data[].category`          | `String`  | 게시글의 카테고리입니다.               |
| `data[].title`             | `String`  | 게시글의 제목입니다.                 |
| `data[].clicks`            | `Number`  | 게시글의 조회수 입니다.               |
| `data[].likes`             | `Number`  | 게시글의 좋아요 숫자입니다.             |
| `data[].isClosed`          | `Boolean` | 게시글의 채택 되었다면 true를 반환합니다.   |
| `data[].commentCount`      | `Number`  | 게시글의 댓글 갯수입니다.              |
| `data[].answerCount`       | `Number`  | 게시글의 답변 갯수입니다.              |
| `data[].createdAt`         | `String`  | 게시글이 생성된 날짜입니다.             |
| `data[].lastModifiedAt`    | `String`  | 게시글이 마지막으로 수정한 날짜 입니다.      |
| `data[].tags[].tagId`      | `Number`  | 태그 아이디 입니다.                 |
| `data[].tags[].name`       | `String`  | 태그 이름입니다.                   |
| `data[].userInfo.userId`   | `Number`  | 유저의 아이디입니다.                 |
| `data[].userInfo.nickname` | `String`  | 유저의 닉네임입니다.                 |
| `data[].userInfo.grade`    | `String`  | 유저의 등급입니다.                  |
| `data[].avatar.avatarId`   | `Number`  | 아바타 파일의 아이디 입니다.            |
| `data[].avatar.filename`   | `String`  | 아바타 파일의 이름입니다.              |
| `data[].avatar.remotePath` | `String`  | 아바타 파일의 경로입니다.              |
| `pageInfo.page`            | `Number`  | 현재 보여질 페이지 입니다.             |
| `pageInfo.size`            | `Number`  | 한페이지에 들어갈 게시글의 갯수 입니다.      |
| `pageInfo.totalElements`   | `Number`  | 전체 게시글의 갯수 입니다.             |
| `pageInfo.totalPages`      | `Number`  | 전체 페이지 숫자입니다.               |
| `pageInfo.sort.empty`      | `Boolean` | 페이지가 비여있다면 true를 반환합니다.     |
| `pageInfo.sort.unsorted`   | `Boolean` | 페이지가 정렬되지 않았다면 true를 반환합니다. |
| `pageInfo.sort.sorted`     | `Boolean` | 페이지가 정렬되었다면 true를 반환합니다.    |
