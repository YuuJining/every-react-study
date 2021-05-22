# Nomad Coder - React로 영화 웹사이트 제작
<br>

## :pencil2: How does React work?
- React는 어떻게 HTML에 HTML을 넣고 삭제하는지 알고 있어서 소스코드에 처음부터 HTML을 넣지 않는다. <br>
- 페이지가 로드 될때 빈 페이지가 로드되고, 그 빈페이지에 react가 우리가 작성한 component들을 넣어주게 됨 <br>

    #### => Virtual DOM의 동작
<br>

## :pencil2: JSX
- Before start...
    > What is Component? HTML을 반환하는 function이며 다음과 같은 형태로 사용된다. <br>
    
    ``
    ReactDom.render(<App />)
    ``
- JSX는 이렇게 javascript와 HTML사이의 조합을 가르킨다.
- index.js 내에서 react는 하나의 Componet만 render 할 수 있다. 즉, 인접한 JSX는 사용될 수 없음을 의미한다.