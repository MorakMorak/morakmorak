# Preface

Prohibit unauthorized copying, distribution and publication of this document. If you would like to cite the contents and charts of this document, please specify the source and inform Team Morak(spooningTldkt@gmail.com) of the usage.



## Overview <a href="#_overview" id="_overview"></a>

#### HTTP verbs <a href="#overview-http-verbs" id="overview-http-verbs"></a>

모락모락은 HTTP 메서드와 상태 코드에 있어 표준 HTTP 및 REST 규칙을 최대한 준수하고 있습니다.

| Verb     | Usage                                                          |
| -------- | -------------------------------------------------------------- |
| `GET`    | Used to retrieve a resource                                    |
| `POST`   | Used to create a new resource                                  |
| `PATCH`  | Used to update an existing resource, including partial updates |
| `DELETE` | Used to delete an existing resource                            |

| Status code        | Usage                               |
| ------------------ | ----------------------------------- |
| `200 OK`           | 상태를 성공적으로 처리함.                      |
| `201 Created`      | 새 리소스를 성공적으로 생성함.                   |
| `204 No Content`   | 기존 리소스를 성공적으로 제거하여 반환할 자원이 존재하지 않음. |
| `400 Bad Request`  | 잘못된 요청이므로 서버에서 처리할 수 없음.            |
| `401 UNAUTHORIZED` | 잘못된 요청이므로 서버에서 처리할 수 없음.            |
| `403 FORBIDDEN`    | 권한이 부족하여 요청을 수행할 수 없음.              |
| `404 Not Found`    | 요청한 자원이 존재하지 않음.                    |
| `409 CONFLICT`     | 서버의 규칙에 의해 해당 요청을 수행할 수 없음.         |







