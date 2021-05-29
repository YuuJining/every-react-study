# ch. 4 



###  fetching API(Axios)

---
- axios : fetch 위에 있는 작은 Layer; `npm install axious`

- 리액트에서는 AJAX를 구현하려면 Javascript 내장 객체인 XMLRequest 를 사용 또는 다른 HTTP Client를 사용해야 한다.
- 리액트에서 많이 쓰이는 것 중 하나인 axios 라이브러리 사용한다.


**특징**
- 운영 환경에 따라 브라우저의 XMLHttpRequest 객체 또는 Node.js의 HTTP API 사용
- Promise(ES6) API 사용
- 요청과 응답 데이터의 변형
- HTTP 요청 취소 및 요청과 응답을 JSON 형태로 자동 변경

<br>

### Fetch VS Axios

---


#### Fetch
```javascript
//fetch
const url ='http://localhost3000/test`
const option ={
   method:'POST',
   header:{
     'Accept':'application/json',
     'Content-Type':'application/json';charset=UTP-8'
  },
  body:JSON.stringify({
  	name:'sewon',
    	age:20
  })

  fetch(url,options)
  	.then(response => console.log(response))
```

#### Axios
```javascript
//axios
const option ={
  url ='http://localhost3000/test`
   method:'POST',
   header:{
     'Accept':'application/json',
     'Content-Type':'application/json';charset=UTP-8'
  },
  data:{
  	name:'sewon',
    	age:20
  }

  axios(options)
  	.then(response => console.log(response))
```

차이점
- Fetch()는 body 프로퍼티를 사용하고,axios는 data 프로퍼티를 사용한다.
- Fetch의 url이 Fetch()함수의 인자로 들어가고, axios에서는 url이 option객체로 들어간다.
- Fetch에서 body부분은 stringify()로 되어진다.



### Practice

---


#### App.js

```javascript
class App extends React.Component {
    state = {
        isLoading: true
    };
    getMovies = async () => {
        // {data propertie : {data propertie { movie propertie}}}
        const {data: {data: {movies}}} = await axios.get("https://yts.mx/api/v2/list_movies.json?sort_by=rating"); // data 추출
        console.log(movies);
        this.setState({movies, isLoading: false}) // state isLoading propertie를 false로 바꿔라.

    }

    async componentDidMount() {
        // App Componet 가 DidMount 되면 해당 App객체 안에 있는 getMovies를 메소드를 호출한다.(비동기적으로)
        this.getMovies();
    }
    // Page rendering ... 
    render() {
        const {isLoading, movies} = this.state;
        // Mount가 되고 나서 비동기적으로 getMovies 가 호출되고 해당 데이터안에 data 프로퍼티 그 안에 data 프로퍼티 그 안에 movies에 대한 데이터를 추출해서 setting한다.
        return (
            <section className={"container"}>
                {/*<h1> render 하면 호출되는 라이프 사이클 매소드 : DidMount</h1>*/}
                <div> {isLoading ? (
                    <div className={"loader"}>
                        <span className="{loader__text">Loading...</span>
                    </div>
                ) : (
                    // moives라는 데이터를 매핑해서 (Movie.js 에 있는 컴포넌트 Movie에 매칭하여 render하라.
                    <div class="movies">
                        {
                            movies.map(movie => {
                            console.log("render "+ movie);
                            return <Movie year={movie.year} title={movie.title} summary={movie.summary}
                                          poster={movie.medium_cover_image} genres={movie.genres}/>
                                            })
                        }

                    </div>
                )
                }</div>
            </section>
        );
    }
}


export default App;
```


#### Movie.js 
```javascript
import React from "react";
import PropTypes from "prop-types";

function Movie({ year, title, summary, poster, genres}) {
    return (
        <div class="movie">
            <img src={poster}  alt={title} title={title} />
            <div className="{moive__data}">
                <h3 className="{movie__title}"> title :{title} </h3>
                <h5 className="{movie__year}"><b>year</b> : {year} </h5>
                <b> genre </b>  :
                <ul className="genres" > <b>  </b>
                    {genres.map((genre,index)=>
                        <li key ={index} className={"genres_genre"}>
                            {genre}
                        </li>
                    )}
                </ul>
                <p className="{movie__summary}"><b>content</b> : {summary} </p>

            </div>
        </div>
    );
}

// 유효성 검사.
Movie.prototype = {
    id: PropTypes.number.isRequired,
    year: PropTypes.number.isRequired,
    title: PropTypes.string.isRequired,
    summary: PropTypes.string.isRequired,
    poster: PropTypes.string.isRequired,
    genres : PropTypes.arrayOf(PropTypes.string).isRequired
}

export default Movie;
```