# React 강의자료

## 1. THE BASICS OF REACT

#### 1) Introduction

- React JS는 UI를 interactive하게 만들어줌. (웹사이트에 상호작용을 만들어줌)





#### 2) React JS의 특징

```html
<!DOCTYPE html>
<html lang="en">
  <body>
    <div id="root"></div>
  </body>
  <script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
  <script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
  <script>
    const root = document.querySelector("#root");
    const span = React.createElement("span", {id:"sexy-span"}, "Hello I'm a span.");
    ReactDOM.render(span, root);
  </script>
</html>
```

- React JS: 어플리케이션이 아주 interactive 하도록 만들어주는 library.
- ReactDOM: 모든 React element들을 HTML body에 둘 수 있도록 해줌.

- render: React element를 가지고 HTML로 만들어 배치한다. (사용자에게 보여준다)

- 강의의 요점: ==React JS는 우리가 해왔던 방식을 거꾸로 한다.==
  - 바닐라 JS: HTML - JavaScript - HTML
  - React: JavaScript - HTML
  - __JavaScript를 이용해 element를 생성했고 React JS가 그걸 HTML로 번역__





#### 3) Events in React

```javascript
const btn = React.createElement(
  "button", 
  {
    onClick: () => console.log("I'm clicked."),
  }, 
  "Click me"
);
```

- 이 하나의 statement만으로 HTML을 만들고 content도 넣고, event listener도 등록.
- Interactive한 어플리케이션에서 하는 작업들 모두가 event들을 감지하는 것이기 때문에 addEventListener를 반복하는 대신 property에서 event를 등록할 수 있게 함





#### 4) JSX

```javascript
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  const Title = (
    <h3 id="title" onMouseEnter={() => console.log("mouse enter")}>
      Hello I'm a Title.
    </h3>
  );
</script>
```

- JSX: HTML에서 사용한 문법과 흡사한 문법을 가지면서 React 요소를 만들어줌
- Babel: 브라우저가 온전히 JSX를 이해하는 것은 아니기 때문에 브라우저가 JSX를 이해할 수 있도록 babel 설치



```javascript
const Container = () => (
  <div>
    <Title />
    <Button />
  </div>
);
ReactDOM.render(<Container />, root)
```

- Title과 Button(React Element)를 Container에 포함시키기 위해 할 일

  1. Title과 Button을 함수로 만들어준다.

     ```react
     function Title () {
       return (
         <h3 id="title" onMouseEnter={() => console.log("Mouse Enter.")}>
           Hello I'm a title
     	</h3>
       );
     }
     const Button = () => (
      <button 
         style={{
           backgroundColor: "tomato",
         }} 
         onClick={() => console.log("I'm clicked.")}
       >
         Click me
       </button>
     )
     ```

  2. 마치 일반적인 HTML 태그인 것처럼 포함시켜주기

     - ==컴포넌트의 첫 글자는 반드시 대문자==
     - 만약 소문자면 React랑 JSX는 이게 HTML button 태그라고 생각

     ```react
     const Container = () => (
       <div>
         <button>Hello</button>
       	<Title />
         <Button />
       </div>
     );
     ReactDOM.render(<Container />, root);
     ```

     



