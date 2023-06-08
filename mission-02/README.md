
🦁 [ 멋사 프론트엔드 스쿨 6기 과제 ]<br />
☼ Mission 02.login 코드 리뷰 ☼

<br />

# *️⃣ HTML Markup image

![Mission 02 login markup](https://github.com/kimInDa/home-work/assets/105577805/e4483f58-0041-496c-ae3d-fe6326c28ca0)

<br />

# *️⃣ 코드 리뷰

## ☼ 제목
- 예제 영역에 대한 제목 '로그인'은 사이트 전체에 대한 제목이 아니므로 h1이 아닌 h2(.login__title) 요소로 마크업합니다.

## ☼ 로그인 정보 입력
- 사용자에게서 정보를 입력받아 서버로 전송하는 아이디&lt;input&gt;, 비밀번호&lt;input&gt;, 로그인 버튼&lt;button&gt;은 &lt;form&gt;의 내부 요소로 마크업 합니다. 
- &lt;form&gt; 요소 내부에는 로그인 정보를 입력하는 영역임을 알려주는 &lt;legend&gt;와 각 입력창&lt;input&gt;에 대한 정보를 알려주는 &lt;lable&gt; 요소를 마크업 하여 접근성을 높입니다.
- &lt;legend&gt; 요소는 화면상에서 보이지 않지만 스크린리더는 읽을 수 있는 숨김컨텐츠가 되도록 CSS 스타일링을 합니다.
- 로그인 버튼은 아이디와 비밀번호 입력칸의 오른쪽에 정렬하기 위하여 display 속성의 absolute 값을 지정해 줍니다. 그리고 로그인 버튼의 부모인 &lt;form&gt;의 display 속성값을 relative로 지정하여 로그인 버튼이 이동하기 위한 기준을 만들어 줍니다. 로그인 버튼에 top: 0과 right: 0으로 이동값을 지정해주어 정렬합니다.

## ☼ 회원 정보 관련 링크
- '회원가입'과 '아이디 비밀번호 찾기'는 사용자에게 다른페이지로의 이동을 제공하므로 &lt;a&gt;요소로 마크업합니다.
- &lt;a&gt;요소는 &lt;ul&gt;과 &lt;li&gt;요소의 자식 요소로 마크업하여 순서가 없는 목록으로 리스트화 합니다.
- &lt;li&gt;의 display 속성값은 list-item으로 외부의 값을 지정하지 않으면 block 유형처럼 표시됩니다. 위아래 정렬된 두 &lt;li&gt;를 가로정렬하기 위해서 float 속성을 사용합니다. '회원가입' &lt;li&gt;의 float에는 left를 '아이디 비밀번호 찾기' &lt;li&gt;의 float에는 right 값을 주어 정렬합니다.

## ☼ &lt;form&gt;과 &lt;a&gt; 구분
- 사용자가 입력한 정보를 서버와 주고 받는 &lt;form&gt;과  사용자에게 링크를 제공하는 &lt;a&gt;는 사용자의 사용 목적과도 구분되는 동시에 요소의 기능 또한 구분됩니다. 따라서 &lt;a&gt;를 &lt;form&gt;에 포함하지 않고 분리합니다.

<br />

# *️⃣ 결과물
![Mission 02 login fin](https://github.com/kimInDa/home-work/assets/105577805/fb5b3d84-c725-4247-b5c4-69515d468a7b)
