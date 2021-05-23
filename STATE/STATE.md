# Nomad Coder - React로 영화 웹사이트 제작
<br>

## :pencil2: Class Component
- function Component VS class Component
    > function Component는 무언가를 return 하지만, class Component는 render method로 동작이 이루어지게 된다. React는 자동으로 class Component의 render method를 실행하게 된다.
- Why Class Component?
    > class Component에서는 state를 사용할 수 있음.


    <br>
## :pencil2: STATE
- state는 동적 데이터들을 사용할 때 만들어지게 된다.
- state는 Component의 data를 넣을 공간인 있고 이 data는 변하게 된다.
- state는 object다.
- render method 바깥에 선언하며, render method 내부에서 사용하기 위해선 this.sate.__ 로 사용하면 된다.
    > this를 사용하는 이유는 class 이기 때문이다.
    
    ``
    state = {
        counter: 0    
    }
`` <br><br>
    ``render() {
        return ``<a> The number is {this.state.counter} </a> 
    ``    
    }``
- 어떻게 state의 data를 바꾸는가?
    > 절대 state의 data를 직접 바꾸지 말자<br>
    > setState() 함수를 이용하자<br>
    > setState() 함수를 이용하게 되면 react에서 자동으로 새로운 state와 함께 render method를 호출해준다. <br>
    > setState() 함수를 이용할 때 외부의 상태에 의존하지 않는 방법은 current를 이용하면 된다.
    
    <br>

## :pencil2: Component Life Cycle
#### 1. Mounting
- render method가 실행되기 전에 js의 constructor()가 실행된다.
- 처음 Component가 rendering 될 때에 componentDidMount() 함수가 호출된다.
#### 2. Updating
- setState를 호출 => component를 호출하고 rendering이 모두 마친 후에 업데이트가 종료 => componentDidUpdate() 실행
#### 3. Unmounting
- componentWillUnmount()    
