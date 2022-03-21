# 🥹 Kimbug CSS Final Project

Kimbug님의 강의를 들으면서 최종 프로젝트를 진행했다.  
내가 작성한 코드와 Kimbug님의 코드가 많이 달랐기에, 복습을 위해 Kimbug님 코드를 살펴볼 예정이다.

우선 모바일 시안과 데스크톱 시안이 둘 다 있었기 때문에, 모바일 시안부터 제작을 시작한다.  
본 프로젝트에서는 Bootstrap의 Grid System을 활용한다.

모바일 시안은 iPhone 5/SE 화면 크기를 기준으로 했다.  
또한, Grid System의 maximum container 사이즈를 960px로 제한하며,  
모바일과 데스크톱 간 Break Points를 768px로 설정한다.

# 사전 작업

CSS 작업을 시작하기 전에 필요한 스타일을 미리 적용해놓기도 하고, Reset CSS라고 해서 불필요한 스타일을 미리 제거하기도 한다.  
일반적인 방법은 Eric Meyer라는 사람이 만들어놓은 리셋 방법을 복사해서 사용하는 것이지만, 원치않는 부분까지 건드려버릴 수 있으므로 직접 만들어서 사용하는 방법도 있다.  
초대형 프로젝트는 아니므로 직접 만들어서 사용해보자.  
주석으로 달아놓은 설명을 읽어보자.

```css
* {
  box-sizing: border-box;
  margin: 0;
}

body {
  font-family: "DM Sans", sans-serif;
}

/* Reset CSS */
a {
  text-decoration: none;
  /* 부모의 color를 상속받게 함 */
  color: inherit;
}

/* form 관련 태그는 font-family가 안 먹힐 때가 있으므로 따로 명시함 */
button,
input,
textarea {
  font-family: "DM Sans", sans-serif;
  /* 이 태그들은 글자 크기가 기본적으로 작아서 일단 잘 보이게 설정 */
  font-size: 16px;
}

/* 클릭했을 때 나오는 강조 테두리 없애기 */
button:focus,
button:active,
input:focus,
input:active,
textarea:focus,
textarea:active {
  box-shadow: none;
  outline: none;
}

/* 리스트 스타일을 없애고, 여백을 삭제함 */
ul,
ol,
li {
  list-style-type: none;
  padding-left: 0;
  margin-left: 0;
}
```

이번에는, 이제부터 만들 시안에 공통적으로 적용되는 부분을 찾아서 미리 설정해놓는다.  
보통 시안이 주어졌을 때 전체적으로 훑어보면서 공통적인 부분을 미리 캐치해서 설정 해놓는 경우도 있다고 한다.

```css
p {
  font-size: 16px;
  line-height: 1.5;
  color: #2b292d;
  letter-spacing: -0.01em;
}

h1 {
  color: #2b292d;
}

/* button은 보통 반복되는 경우가 많기 때문에 시안을 살펴본 뒤 공통적으로 쓰일 클래스에 정의하자 */
.fill-button {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: 140px;
  height: 48px;
  border: none;
  background-color: #3040c4;
  color: white;
  font-size: 15px;
  line-height: 1.6;
  font-weight: 700;
  letter-spacing: -0.05em;
  border-radius: 2px;
  transition: opacity 300ms ease-in-out;
}

.fill-button.inverted {
  color: #3040c4;
  background-color: white;
}

.fill-button:hover {
  opacity: 0.5;
}

.section {
  padding: 80px 0;
}

.section-category {
  display: block;
  font-size: 16px;
  line-height: 1.5;
  letter-spacing: -0.01em;
  text-transform: capitalize;
  margin-bottom: 8px;
}

.section-title {
  font-size: 34px;
  line-height: 1.0588235294;
  letter-spacing: -0.03em;
  color: #2b292d;
  margin-bottom: 24px;
}
```

# 📱 모바일 시안

## 1. landing part

<img width="324" alt="스크린샷 2022-03-21 오전 10 18 15" src="https://user-images.githubusercontent.com/86224851/159194644-5febbd4f-e2cd-4177-9e9f-6796d122308a.png">

<img width="869" alt="스크린샷 2022-03-21 오전 10 20 06" src="https://user-images.githubusercontent.com/86224851/159194725-e15ba858-4ef2-4223-a6e7-b767a26bf703.png">

모바일 시안과 데스크톱 시안 모두 모든 칸의 Grid를 사용하므로 col-12를 사용한다.

```html
<div class="container">
  <div class="row">
    <div class="col-12"></div>
  </div>
</div>
```

두 시안 모두 메인 타이틀에서 쉼표 기준으로 줄을 띄우는 것을 볼 수 있다.  
보통 이렇게 디자이너 분이 줄간격을 의도적으로 넣은 것 같다면 br 태그를 사용해서 확실하게 띄워주는 것이 좋다.

```html
<h1 class="landing-title">
  Change your career,<br />
  Change your life
</h1>
```

위에서 미리 공통 스타일로 만들어놨던 .fill-button을 .landing 안에 있는 것들로 특정하기 위해서 따로 .button-group을 만들어서 감싸주었다.

```html
<div class="button-group">
  <a class="fill-button" href="#">Apply now</a>
  <a class="fill-button inverted" href="#">Learn more</a>
</div>
```

## 2. service part

<img width="325" alt="스크린샷 2022-03-21 오후 6 25 42" src="https://user-images.githubusercontent.com/86224851/159234150-6630bd2d-a3de-4372-919a-ff80325f9b77.png">

<img width="867" alt="스크린샷 2022-03-21 오후 6 26 15" src="https://user-images.githubusercontent.com/86224851/159234246-ef5ebdcf-24b1-498e-ad44-6218fdafbc65.png">

모바일 시안에서는 모든 칸의 Grid를 사용하는 반면, 데스크톱 시안에서는 각각의 컨텐츠가 6칸씩 차지하므로 col-md-6를 클래스에 추가해준다.  
이렇게 되면 화면이 md 사이즈가 넘어갈 때 컨텐츠가 자동으로 한 줄에 표시되게 될 것이다.

```html
<div class="container">
  <div class="row">
    <div class="col-12 col-md-6">
      <!-- content -->
    </div>
    <div class="col-12 col-md-6">
      <!-- content -->
    </div>
  </div>
</div>
```

만약, 두 컨텐츠 간 간격을 주기 위해서 margin-bottom을 사용했다고 하면, 아래쪽 컨텐츠에도 적용이 되어서 화면 크기가 의도대로 맞춰지지 않을 수 있다.  
따라서 가상 클래스를 사용해서 특정한 컨텐츠에만 margin을 적용했다.

```css
.service .col-12:first-child {
  margin-bottom: 40px;
}
```

## 3. program part

<img src="https://user-images.githubusercontent.com/86224851/159237515-f2d95556-1aea-4e3e-883e-15d8757d65ba.gif">

<img width="865" alt="스크린샷 2022-03-21 오후 6 45 13" src="https://user-images.githubusercontent.com/86224851/159237200-75bbef94-a375-4e60-b408-5c79a10a7b1b.png">

텍스트가 있는 파트는 모바일 시안에서는 모든 칸을 사용하지만, 데스크톱 시안에서는 10칸만 사용하기 때문에 col-12, col-md-10을 클래스에 넣어줬다.  
또한, col-md-10을 사용하게 되면 왼쪽에서부터 칸을 채우기 때문에 컨텐츠가 가운데에 오지 않는다. Bootstrap에서는 이를 간편하게 정렬하기 위해서 다양한 클래스를 지원한다.  
텍스트 파트 전체의 정렬이므로 부모 요소인 .row에 flex와 justify-content: center;를 부여하는 justify-content-center 클래스를 추가해줬다.

```html
<div class="container">
  <div class="row justify-content-center">
    <div class="col-12 col-md-10">
      <!-- content -->
    </div>
    <div class="row">
      <div class="col-12 col-md-4">
        <!-- content -->
      </div>
      <div class="col-12 col-md-4">
        <!-- content -->
      </div>
      <div class="col-12 col-md-4">
        <!-- content -->
      </div>
    </div>
  </div>
</div>
```

program part와 다음에 나올 curriculum part는 디자인이 굉장히 유사하다.  
작업할 때 이렇게 유사한 디자인이 있다면, 공통적인 부분을 추려서 미리 설정을 해놓는다고 위에서 언급한 바 있다.  
공통되는 부분은 .section으로 표시해서 스타일을 적용하였다.

a 태그와 이미지를 표시하는 파트는 모바일 시안에서는 모든 칸을 사용하므로 col-12, 데스크톱 시안에서는 4칸씩 사용하므로 col-md-4를 클래스로 입력했다.

위에서 가상 클래스를 활용해서 원하는 요소에만 margin 등의 속성을 부여했다고 했다.  
그런데 만약, 요소가 너무 여러 개여서 오히려 전체에 속성을 주고, 몇 개만 그 것을 제거하는게 나을 때도 있다.  
이는 상황에 따라 다르므로 많이 연습해봐야겠다.

## 4. curriculum part

<img width="327" alt="스크린샷 2022-03-21 오후 7 14 15" src="https://user-images.githubusercontent.com/86224851/159241463-12ec90ae-a62d-4181-abc0-f6401001cecf.png">

<img width="865" alt="스크린샷 2022-03-21 오후 7 13 44" src="https://user-images.githubusercontent.com/86224851/159241382-9192fe8d-954a-49e1-952d-16cbcda8ce28.png">

이 파트는 텍스트 부분은 program part와 매우 유사하다. 따라서 .section으로 통합하여 스타일을 만들어줬었다.  
모바일 시안과 데스크톱 시안에서 눈에 띄는 차이점은 바로 이미지의 유무이다.  
이로 인해서 Grid를 어떤 식으로 설정해야 두 시안 사이를 원활하게 코딩할 수 있는지 고민해야한다.  
데스크톱 시안까지 고려하면 하나의 row에 a 태그까지를 하나의 묶음, 이미지를 하나의 묶음으로해서 col-md-6를 사용하고, 두번째 row에는 텍스트 하나하나를 col-md-6를 사용해 묶으면 될 것 같다.

```html
<div class="container">
  <div class="row align-items-center">
    <div class="col-12 col-md-6">
      <!-- content -->
    </div>
    <div class="col-12 col-md-6">
      <!-- image -->
    </div>
  </div>
  <div class="row">
    <div class="col-12 col-md-6">
      <!-- content -->
    </div>
    <div class="col-12 col-md-6">
      <!-- content -->
    </div>
  </div>
</div>
```

만약 두 번째 row에 있는 col-12에만 속성을 적용하고싶으면 어떻게 해야할까?  
클래스를 지정하는 것도 방법이지만 위 코드 그대로인 상태로 사용한다면 아래와 같을 것이다.

```css
.curriculum .row:last-child .col-12:first-child {
  margin-bottom: 40px;
}
```

다소 길긴 하지만 가상 클래스를 계속 적용해서 요소를 선택할 수도 있다는 것을 알고 넘어가자.

## 5. subscription part

<img width="325" alt="스크린샷 2022-03-21 오후 9 00 15" src="https://user-images.githubusercontent.com/86224851/159256911-0c0f1bf0-ff6e-405e-ab9f-72defb688c11.png">

<img width="866" alt="스크린샷 2022-03-21 오후 8 59 29" src="https://user-images.githubusercontent.com/86224851/159256782-ec73b93c-61ce-470b-ba6b-bb559e8e04a0.png">

모바일 시안에서는 컨텐츠 하나하나가 모든 칸을 사용하므로 col-12를 사용했다.  
데스크톱 시안에서는 이미지가 하나의 공간, 텍스트와 form이 하나의 공간을 가지는 것으로 보이므로 크게 두 묶음으로 나눌 수 있을 것 같다.  
두 묶음 각각은 5칸, 7칸을 사용하여 하나의 row에 들어올 수 있게 만들었다.

```html
<div class="container">
  <div class="row align-items-center">
    <div class="col-12 col-md-5"></div>
    <div class="col-12 col-md-7"></div>
  </div>
</div>
```

```html
<form class="subscription-form" action="">
  <div class="input-group">
    <input type="email" placeholder="Enter your email" />
    <button class="fill-button" type="submit">Get started</button>
  </div>
</form>
```

지금까지 .fill-button을 통해서 a 태그를 공통적으로 꾸며왔다.  
그런데 시안을 보아하니... 이 파트에서는 a 태그가 아니라 button 태그로 사용해야 할 것 같다.  
문제는 a 태그에 맞춰 스타일을 만들어놔서 button 태그에 스타일을 입히면 이상하다는 것이다.  
이럴 경우, 스타일을 다른걸 다시 만들거나 해야하는 것은 아니고 그냥 공통 스타일을 입힌 상태에서 button 태그에 대해서만 스타일을 추가해주면 된다.

## 6. footer part

<img width="321" alt="스크린샷 2022-03-21 오후 9 14 02" src="https://user-images.githubusercontent.com/86224851/159258776-099f5f17-8bc5-478a-b640-ec192b97741e.png">

<img width="866" alt="스크린샷 2022-03-21 오후 9 14 48" src="https://user-images.githubusercontent.com/86224851/159258874-939fc9c0-d5ea-4d60-9a60-7999acfe1c61.png">

모바일 시안에서는 아래로 내려가는 형식이지만, 데스크톱 시안에서는 옆으로 늘어지는 형식이다.  
딱히 전체 크기를 사용한다고 해도 아래로 내려가거나, 옆으로 늘어지는 형태에 영향을 주지 않으므로 전체 칸을 사용하는 것으로 했다.

```html
<div class="container">
  <div class="row">
    <div class="col-12">
      <ul class="footer-links">
        <li class="footer-link">
          <a href="#">Terms</a>
        </li>
        <li class="footer-link">
          <a href="#">Privacy</a>
        </li>
        <li class="footer-link">
          <a href="#">License</a>
        </li>
      </ul>
    </div>
  </div>
</div>
```

## 좀 더 살펴볼만한 것?

서론 부분에서 "또한, Grid System의 maximum container 사이즈를 960px로 제한하며..."라고 언급했었다.  
이게 무슨 말인고 하니, Bootstrap의 Grid System이 적용되는 화면의 크기의 Break points가 1200px로 넘어가도 Grid System이 적용되는 부분의 크기를 960px로 제한하겠다는 것이다.  
만약, 이 제한을 걸지 않았다면 요소들이 좀 더 옆으로 늘어난 형태로 우리 눈에 보였을거라 예상된다.  
아래와 같은 코드로 이러한 제한을 구현한다.

```css
@media screen and (min-width: 1200px) {
  .container {
    max-width: 960px !important;
  }
}
```

이상으로 Kimbug CSS Final Project 리뷰를 마치도록 하겠습니다.  
시안 파일과 더불어 어떤 식으로 Grid System을 사용하는지 사고하는 기초를 다지는데 도움이 되었다.  
🥳 수고하셨습니다~
