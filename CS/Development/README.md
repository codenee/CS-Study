# Part 1-1 Development
- [Part 1-1 Development](#part-1-1-Development)
  - [REST API](#REST-API)

   

[back](https://github.com/codenee/CS-Study)

</br>

## 개발 상식
### REST API
Representational State Transfer
* 분산 네트워크 상에서 자원(리소스)을 표현하고 그 상태를 전송하는 아키텍처 스타일.
* 서버 자원을 클라이언트에 구애받지 않고 사용할 수 있게 하는 설계 방식.
* 클라이언트에서 정보를 요청하면 서버는 특정 기기에 종속되지 않고 모든 기기에 통용할 수 있는 JSON데이터를 응답으로 보냅니다.
* 서버가 클라이언트의 요청에 체계적으로 대응할 수 있어서 서버 프로그램의 재사용과 확장성이 좋아집니다.

#### REST
* HTTP URL로 서버의 자원을 명시하고, HTTP메서드(POST, GET, PATCH/PUT, DELETE)로 해당 자원에 대해 CRUD하는 것을 말합니다.

#### API
* 클라이언트가 서버의 자원을 요청할 수 있도록 서버에서 제공하는 인터페이스입니다.

#### REST API 특징
* 자원(Resources)
  * REST에서는 모든 자원을 고유한 식별자(URI)를 통해 표현.
  * 웹의 자원은 각각의 URI로 식별되며(/users), 이러한 지원은 서버에 의해 관리됨.
* 표현(Representation)
  * 자원의 상태는 다양한 표현으로 나타낼 수 있다.
  * 주로 JSON 또는 XML형식의 데이터를 사용한다.
  * 클라이언트는 이러한 표현을 통해 서버와 상호작용한다.
* 상태 전이(Stateless)
  * REST는 상태를 유지하지 않는(Stateless)특징을 가지고 있다.
  * 각 요청은 모든 필요한 정보를 포함하고 있어야 하며, 서버는 요청을 처리하기 위해 필요한 정보만을 이용.
  * 세션 상태는 서버에 저장되지 않고 클라이언트에 의해 유지되어야 한다.
* 인터페이스 일관성(Uniform Interface)
  * REST는 일관된 인터페이스를 제공.
  * 자원에 대한 표준화된 인터페이스로서, CRUD연산을 통해 자원을 조작한다.
  * 이로써 서버와 클라이언트 간의 상호 운용성을 높이게 된다.
    
</br>

위의 4가지 특징(혹은 self-descriptive, HATEOAS)을 엄격하게 지키는 API를 보고 "RESTful API" 라고 한다.

</br>

#### 자원 식별
* REST API의 좋은 예와 나쁜 예

| API  | GOOD  | BAD  |
|---|---|---|
| 글 조회  | GET /post/{id}  | GET /get/posts/{id} |
| 글 생성  | POST /posts  |  POST /posts/create |
| 글 삭제  | DELETE /posts/{id}  |  DELETE /posts/delete/{id} |


#### 데이터 표현
* JSON데이터는 자바스크립트 방식을 차용한 객체 표현식으로, Key와 Value쌍으로 이루어진 속성(property)로 구성된다.
* {"key" : "value"}

#### 상태 전이
* REST API는 서버가 클라이언트의 상태를 저장하지 않습니다.
* HTTP 메서드를 통해 클라이언트와 서버 간의 상태 전이를 일으켜 통신을 효과적으로 할 수 있도록 합니다.

#### 인터페이스 일관성
* REST API는 일관된 인터페이스를 제공하기 위해 HTTP메서드와 URI를 일관성있게 사용한다.

|Method|URI|
|---|---|
|POST| /posts|
|PATCH| /posts/{postId}|
|DELETE| /posts/{postId}|

위와 같이 게시물 생성, 수정, 삭제 URI를 일관성있게 사용합니다.

</br>

>올바르지 않는 방법
>>POST /posts/create </br>
>>PATCH /posts/update/{postId} </br>
>>이렇게 사용하면 안된다고 합니다.



</br>



<!--

**굵게**
***굵은 기울임체***
__밑줄
~~취소선
'코드 블록'

'''
여러 줄
코드 블록
'''

>블록 따옴표

>>여러줄
블록 따옴표

--!>



