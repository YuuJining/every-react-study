# React 1주차

---

React란
- 페이스북에서 제공해주는 front 라이브러리다.
- 컴포넌트 기반으로서 컴포넌트에 데이터를 내려주면 개발자가 설계한대로 UL가 생성된다.

특징
- **컴포넌트**
    - 재사용성에 특화
    - 유지보수에 용이. (한개의 역할만 할수 있도록 결합도가 낮고 응집성은 높게)
    - 컴포넌트의 종류는 클래스형(stateFul) 과 (stateless)으로 나누어진다.

      <br>
- **One Wat Data Flow**
    - 데이터의 방향이 오직 한방향이다.(데이터가 내려가기만 하고 올려 줄 수는 없다.)
    - 부모의 데이터를 바꾸기 위해서는 State?를 사용해요 한다.

    <br>

- **Props and state**
    - props
        - props 란 부모 컴포넌트에 자식 컴포넌트로 전달해 주는 데이터를 말한다.
        - prorps 는 읽기 전용 데이터 이다.
        - 자식 컴포넌트에게 전달 받은 props를 변경이 불가능하고 props를 전달해준 최상위 부모 컴포넌트만 props를 변경할 수 있다.
    - state
        - 동적인 데이터를 다룰 때 사용.
        - 사용자와 상호작용을 통해 데이터를 동적으로 변경해야 할 때 사용.
        - 클래스형 컴포넌트에서만 사용할 수 있는데 각각의 state는 독립적이라 다른 컴포넌트의 직접적인 접근은 불가능하다.
            - 그러나 자신보다 상위에 있는 state는 변경이 가능하고 state를 변경해주는 함수를 props로 받는다면 state변경이 가능.
            - 주의할 점은 props로 넘겨줄 때에 This의 binding에 기울여야 한다.

    <br>
- **virtualDom**
    - 가상의 Document Object Model을 말한다.
    - 일반적으로 HTML 코드를 짜고 웹 에서 열면 html코드들이 dom을 만든다.
        - 만약 html 코드의 일 부분이 변경된다면 전체 Dom을 새롭게 만드는 비효율적인 일이 발생한다.
        - 리액트는 가상의 Dom을 만들어 진짜 Dom과 비교하면 변경사항이 있을 경우만 dom에 반영한다.
        - 앱의 효율성과 속도를 높일 수 있다.



### npm 이란

---
Node Package Manager, Node.js에서 사용하는 패키지를 다운 받을 수 있는 프로그램

**Node.js의 의존성과 패키지 관리를 위한 패키지 매니저**
### npx 이란

---
npm 5.2.0 버전부터 따라오는 프로그램으로, 패키지를 설치하지않고, 1회성으로 실행해 볼수 있게 해준다

        1. 기본적으로 실행되어야할 패키지가 경로에 있는지 먼저 확인합니다.(예: 우리의 프로젝트);
        
        2. 경로에 제대로 있다면, 그대로 실행합니다;
        
        3. 그렇지 않다면 패키지는 설치되어 있지 않다는 걸 의미하고, npx가 최신 버전의 패키지를 설치를 한 후에 실행합니다;


(npm 사용)npm run my-package (pacakge.json 스크립트 수정하고 실행해야 함.)
(npx 사용)npx my-package

### JsonPack 이란

---
npm에서 여러가지 패키지를 설치하면,

dependencies (의존성)에, 패키지 이름과 버전이 저장되어

나중에 package.json 파일만 있으면, 언제 어디서든 같은 개발 환경을 만들 수 있게 해준다.


※ JSX = JS와 HTML의 사이의 조합.


## Practice

---

```javascript

import React from 'react'; // default
import ReactDOM from 'react-dom'; // 가상 Dom객체 ( html에 js 삽입)
import App from './App'; // 내가 정의한 Js file import

ReactDOM.render(<App />,document.getElementById('go'));
// 내가 작성한 App.js 를 id가 go인 곳에 삽입래하.

```


```javascript
import React from "react";
import PropTypes from "prop-types";

function Food({name, image,rating}) {
    // component
    return (
        <div>
            <h3> I like :{name}</h3>
            <h4> {rating} / 5.0</h4>
            <img sizes={20} src={image} alt={name}/>
        </div>
    );
}
// validation Check
Food.prototype={
    // want i get type decription
    name : PropTypes.string.isRequired,
    picture : PropTypes.string.isRequired,
    rating : PropTypes.number.isRequired
}

function Component2(Props) {
    return (<h2>Component2 : {Props.age}</h2>)
}


// dynamic date
const FoodILike = [
    {
        id:1,
        name: "Kimchi",
        image:
            "http://aeriskitchen.com/wp-content/uploads/2008/09/kimchi_bokkeumbap_02-.jpg"
        ,rating : "4"
    },
    {
        id:2,
        name: "Samgyeopsal",
        image:
            "https://3.bp.blogspot.com/-hKwIBxIVcQw/WfsewX3fhJI/AAAAAAAAALk/yHxnxFXcfx4ZKSfHS_RQNKjw3bAC03AnACLcBGAs/s400/DSC07624.jpg"
        ,rating : 5

    },
    {
        id:3,
        name: "Bibimbap",
        image:
            "http://cdn-image.myrecipes.com/sites/default/files/styles/4_3_horizontal_-_1200x900/public/image/recipes/ck/12/03/bibimbop-ck-x.jpg?itok=RoXlp6Xb"
        ,rating : 4

    },
    {
        id:4,
        name: "Doncasu",
        image:
            "https://s3-media3.fl.yelpcdn.com/bphoto/7F9eTTQ_yxaWIRytAu5feA/ls.jpg"
        ,rating : 1.7

    },
    {
        id:5,
        name: "Kimbap",
        image:
            "http://cdn2.koreanbapsang.com/wp-content/uploads/2012/05/DSC_1238r-e1454170512295.jpg"
        ,rating : 3

    }
];

function renderFood(dish) {
    console.log(dish);
    return  <Food name={dish.name} image={dish.image} rating={dish.rating}/>
}

function App() {
    return (
        // <div>Hello, World<Test/>
        <div>
            <Component2 age="12"/>
            // map List 순회 , dish는 obejct 
            {/*{FoodILike.map(dish => (< Food name={dish.name} image={dish.image}/>))}*/}
            // dish.속성 , 각 매개변수 이름 명시하고 매핑.
            {FoodILike.map(renderFood)}
        </div>
    );
}

export default App; // app.js 등록.

```


**state**

```javascript
// state 실습

class App extends React.Component{
    state ={
        count :0
    };
    add=()=> {
        console.log("add");
        this.setState({count:this.state.count+1});
    };
    minus=()=> {
        console.log("minus");
        this.setState({count:this.state.count-1});

//        this.state.count=-1; // react는 render 함수를 refresh 하지 않는다.
        // state 객체의 count가 변경될 때 render 함수이 호출되기를 원하고 있다.
    };
    reset=()=>{
        this.setState({count:0});
    };
    render() {
        return(<div>
            <h1>React.Component 상속 {this.state.count}</h1>
            <button onClick={this.add}> addCount </button>
            <button onClick={this.minus}> minusCount </button>
            <button onClick={this.reset}> reset </button>
        </div>);
    }
}
```

- React.Component를 상속받은 객체는 많은 기능을 가지고 있다.
- 이 전 까지는 render 함수를 우리가 만들어서 사용했다. 이 해당 객체에 상속만 받으면 우리가 정의할 필요할 없이 갖다가 사용한다.
- add,minus 해당 함수가 동작하기 위해 사용자 화면에 렌더링을 해야한다. state객체의 count 속성을 바꿀 때 refresh 가 필요하다. 그래서 속성만 바꾸고 렌더까지 해줘야 하는 상황이다.
- 그러기 위해서는 setState라는 메소드를 호출하여 객체의 속성값을 바꾸고 새로 rerender까지 하게 된다.


<br>


**Componenet Life Cyecle**

---
1. 메소드 호출 전(Constructor)
2. 메소드 호출
   2.1 메소드 실행 후 (update)(DidMount : render 후)
3. 메소드 호출 끝 (component dead)

```javascript

class App extends React.Component{
    state ={
        count :0
    };
    add=()=> {
        this.setState({count:this.state.count+1});
    };
    minus=()=> {
        this.setState({count:this.state.count-1});
    };
    reset=()=>{
        this.setState({count:0});
    };
    componentDidMount() {
        // render 를 다 한 후
        console.log("componentDidMount");
    }
    componentDidUpdate(prevProps, prevState, snapshot) {
        // 메소드 호출 후
        console.log("update");
    }
    componentWillMount() {
        // componente dead
        console.log("dead component");
    }


    render() {
        return(<div>
            <h1>React.Component 상속 {this.state.count}</h1>
            <button onClick={this.add}> addCount </button>
            <button onClick={this.minus}> minusCount </button>
            <button onClick={this.reset}> reset </button>
        </div>);
    }
}

```


```javascript
class App extends React.Component{
    state={
        isLoading : true
    };
    componentDidMount() {
        console.log("componentDidMount");
        //data fetch !
        setTimeout(()=>{
            this.setState({isLoading : false})
        },5000);
        console.log("dead");
    }

    render() {
        const {isLoading}=this.state;
        return(
            // <h1> render 하면 호출되는 라이프 사이클 매소드 : DidMount</h1>
            <div> {isLoading ? "Loading True" : "Ready Complete"}</div>
        );
    }
}
```

