# React 1주차

---

## How does React work?

- React는 어떻게 HTML에 HTML을 넣고 삭제하는지 알고 있어서 소스코드에 처음부터 HTML을 넣지 않는다.

- 페이지가 로드될 때 빈 페이지가 로드되고, 그 빈 페이지에 react가 우리가 작성한 component들을 넣어주게 된다.

  #### => Virtual DOM의 동작

  

## :pencil: JSX

- Component

  - HTML을 반환하는 function이며 다음과 같은 형태로 사용된다.

  ```javascript
  ReactDom.render(<App />)
  ```

- JSX
  - JSX는 이렇게 javascript와 HTML사이의 조합을 가르킨다.
  - index.js 내에서 react는 하나의 Component만 render 할 수 있다. 즉, 인접한 JSX는 사용될 수 없다.



## :pencil: PROPS

- JSX에서는 Component 간에 정보를 넘겨 줄 수 있는데, 다음과 같이 사용 할 수 있다.

  ```javascript
  <Food name="kimchi" />
  ```

  - 위 코드는 Food 라는 Component에 kimchi를 value로 갖는 prop name을 줬음을 의미한다.

- props의 value로는 string / boolean / array 등을 가질 수 있다.

- props를 console.log로 찍어주게 되면 Object로 찍힌다.

- ES6 => props.fav === { fav }

  - Object props에는 fav 라는 이름의 props가 존재하는데 value를 { fav } 로 표현이 가능하다. (ES6)

- jsx props의 조합으로 재사용이 가능한 Component들을 만들 수 있다.

- map함수를 이용해 props의 value값들을 컴포넌트에 뿌려줄 수 있다.



### 	PropTypes

- prop-types는 내가 전달 받은 props가 원하는 props인지 확인하는 역할을 한다.

```javascript
FollowList.propTypes = {
    header: PropTypes.string.isRequired,
    data: PropTypes.array.isRequired
};
```



## :pencil: STATE

- function Component VS class Component
  - function Component는 무언가를 return 하지만, class Component는 render method로 동작이 이루어지게 된다. React는 자동으로 class Component의 render method를 실행하게 된다.
- Why Class Component?
  - Class Component에서는 state를 사용할 수 있음.
    - function Component에서 hook 사용하면 대체 가능함.



- state

  - state는 동적 데이터들을 사용할 때 만들어지게 된다.

  - state는 Component의 data를 넣을 공간이 있고 이 data는 변하게 된다.

  - state는 Object이다.

  - render method 바깥에 선언하며, render method 내부에서 사용하기 위해선 this.state._로 사용하면 된다.

    - class 이기 때문!

    ```javascript
    state = {
    		counter: 0
    }
    
    render() {
    		return <a> The number is {this.state.counter} </a>
    }
    ```

  - 어떻게 state의 data를 바꾸는가?
    - state의 data를 직접 바꾸지 마라!! 절대!!
    - setState() 함수를 이용하자.
    - setState() 함수를 이용하게 되면 react에서 자동으로 새로운 state와 함께 render method를 호출해준다.
    - setState() 함수를 이용 할 때 외부의 상태에 의존하지 않는 방법은 current를 이용하면 된다.



## :pencil: Component Life Cycle

- 1. Mounting
     - render method가 실행되기 전에 js의 constructor()가 실행된다.
     - 처음 component가 rendering 될 때에 componentDidMount() 함수가 호출된다.
  2. Updating
     - setState() 를 호출 -> component를 호출하고 rendering이 모두 마친 후에 업데이트가 종료 -> componentDidUpdate() 실행
  3. Unmounting
     - componentWillUnmount()