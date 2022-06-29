# 단위를 환산해 주는 사이트

## 1️⃣ 첫번째 시도 구현

시간을 단위로 바꿔주는 사이트를 만들었다.
<img width="419" alt="스크린샷 2022-06-29 오후 3 34 17" src="https://user-images.githubusercontent.com/67817682/176367814-4f9f603e-b511-43e2-9879-d2573f827ca3.png">

## ⏱ 구현 기능 ⏱

- 시간을 분으로 바꿔주는 기능
- 분을 시간으로 바꿔주는 기능
- "분으로", "시간으로" 버튼을 눌를 때 마다 input 값이 바뀌도록 설정
- Reset 기능

## 🔁 input을 비활성화 🔁

input 속성 중 *disabled*가 둘 중 하나만 *False*가 가능하도록 해야한다.
flag 변수에 True, False를 설정해서 한 쪽 input 값만 활성화 시켰다.

## 🎪 총 3가지 이벤트함수 생성 🎪

React에 *State*를 활용해서 변수가 동적으로 바뀌도록 설정

- onchange 이벤트 함수

  - 시간이 입력되면 onChange 함수가 실행되어 setTime의 state data 값이 변경된다.

- reset 이벤트 함수

  - reset 버튼이 눌러지면, setTime의 state data 값이 0으로 변경된다.

- flip 함수
  - **_"분으로"_** , **_"시간으로"_** 버튼을 눌르면 flag state data 값이 False -> True, True -> False로 변경된다.

</details>

---

## 2️⃣ 두번째 구현 시도

시간 뿐만 아니라 더 많은 단위에 대해서도 환산이 가능하도록 시도하고 싶었다.

<img width="419" alt="스크린샷 2022-06-29 오후 6 06 43" src="https://user-images.githubusercontent.com/67817682/176399425-476b9d3c-9c2f-4f0b-ace4-c4eb561d7301.png">

---

<img width="419" alt="스크린샷 2022-06-29 오후 6 06 47" src="https://user-images.githubusercontent.com/67817682/176399588-f9aa25c7-2a14-40f7-9301-19f8ba2930f9.png">

---


<img width="419" alt="스크린샷 2022-06-29 오후 6 17 50" src="https://user-images.githubusercontent.com/67817682/176400621-c9c67a97-a8d0-4c64-9d36-fbc7c74e6b6b.png">

## ❗️ 추가 구현 기능 ❗️

- 셀렉트박스(select) 변경 이벤트 처리
  - 메뉴를 만들어 원하는 단위 환산 기능을 사용도록함
  - 거리 단위 환산 기능
  - 부피 단위 환산 기능

## 📜 메뉴 기능 구현 📜

html option 태그를 사용했다.
이때 주의할 점은 option은 꼭 select 태그 안에 들어와야 한다.

```html
<select onClick="{changeMenu}" name="" id="">
  <option value="0">시 분 바꿔줘</option>
  <option value="1">리터 미리리터 바꿔줘</option>
  <option value="2">미터 킬로미터 바꿔줘</option>
</select>
```

## 🐛 버그 🐛

- 메뉴를 바꾼 후에 바로 화면이 바뀌는 것이 아니라 메뉴 버튼은 한 번 더 눌러야 버튼이 바뀐다.

```html
<div>
  <select value="{idMenu}" onChange="{changeMenu}">
    <option value="0">시 분 바꿔줘</option>
    <option value="0">시 분 바꿔줘</option>
    <option value="1">리터 미리리터 바꿔줘</option>
    <option value="2">미터 킬로미터 바꿔줘</option>
  </select>
  {console.log(idMenu)} {idMenu === "0" ? <time /> : null} {idMenu === "1" ?
  <Liter /> : null}
</div>
```

> option을 클릭하면 value값이 바뀔 것이라 예상하고 onClick 어트리뷰트를 사용했지만, 셀렉트박스(select) 변경 이벤트 처리는 onChange를 사용한다.

---

## 3️⃣ 세번째 구현 시도

첫 화면에 바로 "시 분 바꿔줘"로 메뉴가 설정되어 있지만, 화면이 비어있다.

⛔️ 변경 이전 화면

<img width="419"  alt="스크린샷 2022-06-29 오후 6 38 34" src="https://user-images.githubusercontent.com/67817682/176405014-f30ebba0-efb6-4be5-a3b0-359871425a53.png">

✅ 변경 이후 화면

<img width="419" alt="스크린샷 2022-06-29 오후 6 46 13" src="https://user-images.githubusercontent.com/67817682/176406606-da2d6350-d1a7-4a0e-815e-46f5bd39b6c2.png">

## 🐛 버그 🐛

하나의 옵션(option)을 추가해서 새로운 value 값을 선택했지만, re-render 이전이기 때문에
옵션(option)이 변경되지 않았다.

> menuId의 초기값으로 초기 option의 value를 설정하여 실행을 가능하도록 했다.

menuId의 실행 경로를 되짚어 봤고, menuId가 시작하는 시초가 어디인지 살펴봤다. 등잔 밑이 어둡다고 초기값은 생각하지 못하고 전혀 찾지 못했지만, 열번의 확인 이후 **_초기값_**이라는 해결책을 찾을 수 있었다.
