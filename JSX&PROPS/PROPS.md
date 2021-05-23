# Nomad Coder - React로 영화 웹사이트 제작
<br>

## :pencil2: PROPS
- jsx에서는 Component 간에 정보를 넘겨 줄 수 있는데, 다음과 같이 사용할 수있다.

    ``
    <Food name="kimchi" />
    ``
    > 위 코드는 Food 라는 Component에 kimchi를 value로 갖는 prop name을 줬음을 뜻한다.
- props의 value로는 string / boolean / array 등을 가질 수 있다.
- props를 console.log로 찍어주게 되면 Object로 찍힌다.
- ES6 => props.fav === { fav } : Object props에는 fav 라는 이름의 props가 존재하는데 value를 { fav } 이렇게 표현할 수 있다.
- jsx props의 조합으로 재사용이 가능한 Component들을 만들 수 있다.
- js의 map함수를 이용해 props의 value값들을 컴포넌트에 뿌려줄 수 있다.

<br>

## :pencil2: PropTypes
- prop-types는 내가 전달 받은 props가 원하는 props인지 확인하는 역할을 한다.
