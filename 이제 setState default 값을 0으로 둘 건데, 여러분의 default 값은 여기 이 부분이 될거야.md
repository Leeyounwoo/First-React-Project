이제 setState default 값을 0으로 둘 건데, 여러분의 default 값은 여기 이 부분이 될거야. 이 경우에는 0인거지.

지금까지 한 걸 전부 복습해봅시다.

첫번째로, 우린 이 state를 만들었어. 알다시피 setState의 결과는 array야. 첫 번째 요소는 데이터고, 두 번째 요소는 데이터를 수정하기 위한 함수야.

```react
const [miuntes, setMinutes] = React.useState(0);
const onChange = (event) => {
  setMinutes(event.target.value);
}
```

그 다음으로, 우린 input의 __value__를 __state__로 연결해줬지. 이렇게 해주는 건 아주 유용해. 왜냐하면 어디서든 input의 value를 수정해줄 수 있거든. 

좋아, 그 다음으로 우리는 onChange 함수를 만들어줬어. 이 onChange함수는 데이터를 업데이트 해주는 역할을 해. 알겠지? input에서 리스닝하는 데이터 말이야. 보다시피 input은 스스로 업데이트를 해. change 이벤트가 일어났을 때, 즉, 사용자가 input에 뭔가를 써넣을 때, onChange 함수가 실행돼. event.target.value를 얻게 되는데 바로 input value이지. 그 말은 여기 이 데이터가 업데이트 된다는 얘기야. 그 말은 input이 업데이트된단 얘기고. 

input의 value를 연결시켜주는 이유는, 다시 말하자면, input값을 외부에서도 수정해주기 위해서야. 예를 들어, reset 버튼을 누른다고 해보자. 그럼 input 내용을 다 지울 수 있어. 좋아, onChange함수의 주요 포인트는 데이터를 업데이트 해주는 거였어. 예를 들어, 우리가 onChange를 삭제한다고 해도, 여전히 state에 연결된 input 값은 남겨져 있어. 이제 어떻게 되나 봐바. 

```react
<input 
  value={minutes}
  onChange={onChage}
/>
```

예를 들어, 우리가 onChange를 삭제한다고 해도, 여전히 state에 연결된 input 값은 남겨져 있어. 이제 어떻게 되나 봐바. 자 무슨 일이 일어나냐면... 여기에 뭘 쓰려고 하지만... 쓸 수 없어. 그 이유는, 다시 한 번 말하지만, input의 value가 state이고, 이 state의 default 값이 0이기 때문이야. 그리고 방금 onChange 함수를 지웠기 때문에, 이 input이 키보드 이벤트를 감지한다고 해도 업데이트가 이루어지지 않는거지. 좋아. 방금 봤든이 이게 이 두 개 모두가 필요한 이유야. event를 들어주는 것 하나, 그리고 event가 발생했을 때, 값을 업데이트해주고, UI에 보여주는 것 하나. 

```react
const [minutes, setMinutes] = React.useState(0);
const onChange = (event) => {
  setMinutes(event.target.value);
}

<input
  value = {minutes}
/>
```

![image-20211224144538692](C:\Users\LeeYounWoo\AppData\Roaming\Typora\typora-user-images\image-20211224144538692.png)

