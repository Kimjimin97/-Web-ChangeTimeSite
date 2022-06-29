# 시간을 환산해 주는 사이트

<img width="419" alt="스크린샷 2022-06-29 오후 3 34 17" src="https://user-images.githubusercontent.com/67817682/176367814-4f9f603e-b511-43e2-9879-d2573f827ca3.png">

---

## ⏱ 구현 기능 ⏱

- 시간을 분으로 바꿔주는 기능
- 분을 시간으로 바꿔주는 기능
- "분으로", "시간으로" 버튼을 눌를 때 마다 input 값이 바뀌도록 설정
- Reset 기능

---

## 🔁 input을 비활성화 🔁

input 속성 중 *disabled*가 둘 중 하나만 *False*가 가능하도록 해야한다.
flag 변수에 True, False를 설정해서 한 쪽 input 값만 활성화 시켰다.

---

## 🎪 총 3가지 이벤트함수 생성 🎪

React에 *State*를 활용해서 변수가 동적으로 바뀌도록 설정

- onchange 이벤트 함수

  - 시간이 입력되면 onChange 함수가 실행되어 setTime의 state data 값이 변경된다.

- reset 이벤트 함수

  - reset 버튼이 눌러지면, setTime의 state data 값이 0으로 변경된다.

- flip 함수
  - **_"분으로"_** , **_"시간으로"_** 버튼을 눌르면 flag state data 값이 False -> True, True -> False로 변경된다.

```html
const [inputTime, setTime] = React.useState(0); const [flag, changeFlag] =
React.useState(false); const onChange = (event) => {
setTime(event.target.value); }; const reset = () => { setTime(0); }; const flip
= () => { changeFlag((current) => !current); reset(); };
```

---
