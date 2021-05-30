# React 2주차



## AXIOS

- React에는 HTTP Client가 내장되어 있지 않아서 AJAX를 구현하기 위해서는 다른 HTTP Client를 사용해야 한다.

  - 대표적인 것이 Fetch API 와 axios

    > #### AJAX (Asynchronus Javascript And XML)
    >
    > - AJAX란 Javascript 라이브러리 중 하나이며, XMLHttpRequest 객체를 이용해서 전체 페이지를 새로 고침 하지 않고도 페이지의 일부만을 위한 데이터를 로드하는 기법이다.
    > - Javascript를 사용한 비동기 통신, 클라이언트와 서버간에 XML 데이터를 주고받는 기술이다.
    > - Javascript를 통해서 서버에 데이터를 요청하는 것이다.

  

  #### :pencil2: axios VS Fetch API

  - axios

    - 구형 브라우저를 지원한다.

    - JSON 데이터 자동변환이 가능하다.
    - data 프로퍼티를 사용한다.
    - return 값은 Promise 객체 형태이다.

  - fetch

    - 지원하지 않는 브라우저가 있다.
    - Javascript 내장 라이브러리 이기 때문에 import 하지 않고 사용할 수 있다.
    - body 프로퍼티를 사용한다.
    - return 값은 Promise 객체 형태이다.

  

 - axios.get()은 항상 빠르지 않아서 componentDidMount() 에서 사용할 때 데이터를 받아올 때까지 기다려 주어야 함 

    - async / await 사용 => 비동기 처리

      ```javascript
      getMovies = async () => {
      	const {
          data: {
            data: { movies }
          }
        } = await axios.get("https://yts.mx/api/v2/list_movies.json")
      };
      ```

      

## HTTP Methods

클라이언트가 웹서버에게 사용자 요청의 목적/종류를 알리는 수단

Axios 통신하면서 가장 많이 사용되는 메서드들 정리



#### 1. GET

> 입력한 url에 존재하는 자원에 요청을 한다.
>
> 응답은 json 형태로 넘어온다.

```javascript
axios.get("url주소",[,config])
```



#### 2. POST

> 새로운 리소스를 생성할 때 사용한다.
>
> 생성한 data를 서버에 업로드 할 때 사용한다.

```javascript
axios.post("url주소", {
	data 객체
}, [,config])
```



#### 3. DELETE

> REST API 프로그램에서 DB에 저장되어 있는 내용을 삭제하는 목적으로 사용한다.

```javascript
axios.delete("url주소",[,config]);
```



#### 4. PUT

> REST API 프로그램에서 DB에 저장되어 있는 내용을 갱신하는 목적으로 사용한다.

```javascript
axios.put("url주소",data,[,config])
```



출처 : https://velog.io/@shin6403/React-axios%EB%9E%80-feat.-Fetch-API