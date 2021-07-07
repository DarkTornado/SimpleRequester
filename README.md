# SimpleRequester
© 2020-2021 Dark Tornado, All rights reserved.

## Summary / 요약
* Simple HTTP Request Sender for Java/Android.
* 자바/안드로이드용 HTTP 요청 전송 라이브러리

## License / 라이선스
* [BSD 3-Clause License](https://github.com/DarkTornado/SimpleRequester/blob/main/LICENSE)

## Examples / 예시

#### Without Using Method Chaining
```java
SimpleRequester sq = new SimpleRequester(url);   //Create Instance / 인스턴스 생성
sq.setMethod(SimpleRequester.METHOD_POST);       //Set Request Method type / 요청 방식 설정
sq.addHeader("Header name", "Header value");     //Add Header / 헤더 추가
sq.addData("Parameter name", "Parameter value"); //Add Parameter / 파라미터 추가
SimpleRequester.Response = sq.execute();         //Send request and get response / 요청 전송 및 결과 수신
String result = response.body;                   //Get response body / 요청 결과들 중 내용물 가지고 오기
```
#### Using Method Chaining
```java
SimpleRequester.Response response = SimpleRequester.create(url)
    .method(SimpleRequester.METHOD_POST)
    .header("Header name", "Header value")
    .data("Parameter name", "Parameter value")
    .execute();
String result = response.body;
```

<hr>

# API List / API 목록

## class SimpleRequester

### Constructor / 생성자
#####  SimpleRequester();
* Basic Constructor / 기본 생성자
#### SimpleRequester(String url);
* Constructor with url. You can set url to send request when creating an instance
* 인스턴스 생성시 요청을 보낼 url 설정 가능

### Constant / 상수
#### static String METHOD_GET
* Static constant for setMethod(); or method();. Value is `GET`
* setMethod(); or method();에 사용되는 상수. 값은 `GET`.
#### static String METHOD_POST
* Static constant for setMethod(); or method();. Value is `POST`
* setMethod(); or method();에 사용되는 상수. 값은 `POST`.

### Methods / 함수
#### void setUrl(String url);
* Set url to send request.
* 요청을 보낼 url 설정.
#### void setMethod(String method);
* Set requeset method. parameter is `METHOD_GET` or `METHOD_POST`.
* 요청 방식 설정. 인자는 `METHOD_GET` 또는 `METHOD_POST`.
#### void setTimeout(int timeout);
* Set timeoiut. Parameter is millisecond.
* 최대 대기 시간 설정. 그 시간이 지나는 동안 서버가 응답이 없으면 오류로 처리. 인자는 밀리초
#### void setUserAgent(String userAgent);
* Set User-Agent. If you don't set User-Agent, it will use default User-Agent.
* User-Agent 설정. User-Agent를 설정하지 않으면, 기본 User-Agent 사용.
#### void setEncoding(String encoding);
* Set encoding for both of request text and reponse text to `encoding`. Default is  `UTF-8`.
* 요청할 때 보낼 때 인코딩과 받을 때 인코딩을 `encoding`으로 설정. 생략시 `UTF-8` 사용.
#### void setEncoding(String request, String response);
* Set encoding for request text and reponse text. Default is  `UTF-8`.
* 요청할 때 보낼 때 인코딩과 받을 때 인코딩을 따로따로 설정. 생략시 `UTF-8` 사용.
#### void setFollowRedirects(boolean follows);
* Set if to follow the redirect of the requested site or not.
* 요청 대상 사이트의 리다이렉트를 따라갈지 결정.
* Added in version `2.0`. / 버전 `2.0`에서 추가.
#### void addHeader(String key, String value);
* Add request header.
* 요청 헤더 추가.
#### void addData(String key, String value);
* Add request parameter.
* 요청 파라미터 추가.
#### SimpleRequester.Response execute();
* Send HTTP Request and get response.
* HTTP 요청 전송 및 응답 수신.

### Methods can use Method Chaining / 메소드 체이닝이 가능한 메소드들

#### static SimpleRequester create(String url);
* Same as `SimpleRequester(String url)` / `SimpleRequester(String url);` 생성자와 동일.
#### SimpleRequester method(String method);
* Same as `setMethod();` / `setMethod();`와 동일
#### SimpleRequester timeout(int timeout);
* Same as` setTimeout();` / `setTimeout();`과 동일
#### SimpleRequester followRedirects(String key, follows);
* Same as `setFollowRedirects();` / `setFollowRedirects();`와 동일
#### SimpleRequester header(String key, String value);
* Same as `addHeader();` / `addHeader();`와 동일
#### SimpleRequester userAgent(String userAgent);
* Same as `setUserAgent();` / `setUserAgent();`와 동일
#### SimpleRequester encoding(String encoding);
* Same as `setEncoding(encoding);` / `setEncoding(encoding);`과 동일
#### SimpleRequester encoding(String request, String response);
* * Same as `setEncoding(request,. response);` / `setEncoding(request, response);`과 동일
#### SimpleRequester data(String key, String value);
* Same as `addData();` / `addData();`와 동일

## SimpleRequester.Response

####  SimpleRequester.Response(int responseCode, String body);
* Basic Constructor / 기본 생성자

#### int getResponseCode();
* Get HTTP Request's response code. Same as using variable `responseCode` directly
* HTTP 요청을 한 결과의 응답 코드 반환. `responseCode` 변수로 직접 접근 가능
#### int getResponseMessage();
* Get HTTP Request's response code. Same as using variable `msg` directly.
* HTTP 요청을 한 결과의 응답 코드 반환. `msg` 변수로 직접 접근 가능.
* Added in version `2.0`. / 버전 `2.0`에서 추가.
#### String getResponseBody();
* Get HTTP Request's response body. Same as using variable `body` directly
* HTTP 요청을 한 결과 반환. `body` 변수로 직접 접근 가능
#### String toString();
* Return variable `body`. / 변수 `body`의 값 반환

