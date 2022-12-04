# 채용 정보 크롤링(Calendar)

### 1. 캘린더 조회 <a href="#_-_" id="_-_"></a>

#### 1.1. 성공 200 <a href="#_-_200" id="_-_200"></a>

**http-request**

```
GET /calendars HTTP/1.1
Host: docs.api.com
```

**http-response**

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
Content-Length: 420

[ {
  "jobId" : 1,
  "name" : "MorakMorak.LAB",
  "state" : "시작",
  "careerRequirement" : "경력",
  "url" : "https://7357.tistory.com/",
  "startDate" : "2022-01-25",
  "endDate" : "2022-02-02"
}, {
  "jobId" : 1,
  "name" : "MorakMorak.LAB",
  "state" : "시작",
  "careerRequirement" : "경력",
  "url" : "https://7357.tistory.com/",
  "startDate" : "2022-01-25",
  "endDate" : "2022-02-02"
} ]
```

| Path                   | Type     | Description |
| ---------------------- | -------- | ----------- |
| `[].jobId`             | `Number` | DB 시퀀스 키    |
| `[].name`              | `String` | 회사명         |
| `[].careerRequirement` | `String` | 경력 요구사항,    |
| `[].state`             | `String` | 채용 공고 상태    |
| `[].url`               | `String` | 채용 홈페이지 경로  |
| `[].startDate`         | `String` | 체용 신청 시작일   |
| `[].endDate`           | `String` | 채용 접수 마감일   |
