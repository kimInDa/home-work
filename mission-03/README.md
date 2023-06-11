🦁 [ 멋사 프론트엔드 스쿨 6기 과제 ]

❖ Mission 03.transition 코드 리뷰 ❖

<br />
<br />

# *️⃣ HTML Markup image

![Mission 03 transition markup](https://github.com/kimInDa/home-work/assets/105577805/617769cd-eaef-4010-b1a7-c8c420186ff9)

<br />
<br />

# *️⃣ 코드 리뷰
## ❖ 제목

* 예제 영역에 대한 **제목은 &lt;h2&gt;로 마크업** 합니다.
* **사이트**에 대한 글자색을 다르게 주기 위해 **사이트**만 &lt;span&gt;으로 감싸고 폰트 컬러를 지정합니다.
    ```html
        <h2 class="site__title">관련 <span class="title--textOrange">사이트</span></h2>
    ```
    ```css
        .site__title .title--textOrange { color: #ED552F; }
    ```

<br />

## ❖ 리스트

* 사이트 &lt;a&gt;는 **순서가 없는 목록이므로 &lt;ul&gt;과 &lt;li&gt;로 마크업** 합니다.
    ```html
        <ul class="site__list">
          <li class="site__item"><a href="/" class="site__link">제로베이스</a></li>
          <li class="site__item"><a href="/" class="site__link">MDN</a></li>
          <li class="site__item"><a href="/" class="site__link">웹접근성 연구소</a></li>
          <li class="site__item"><a href="/" class="site__link">Web Standards</a></li>
          <li class="site__item"><a href="/" class="site__link">W3C</a></li>
        </ul>
    ```
    <br />
    
* 링크 목록 5개 중 1개만 보이도록 하기 위해서, 링크들의 부모 요소인 **&lt;ul&gt;의 height을 1개의 목록 높이만큼 지정하고, `overflow:hidden;` 속성을 부여**하여 나머지 4개의 링크들을 보이지 않도록 합니다. 
    ```css
        .site__list {
            height: 1.875rem;
            overflow: hidden;
        }
    ```
    <br />
* 마우스를 올리면 목록이 펼쳐지도록 하기 위하여, **transition 속성으로 &lt;ul&gt;의 height를 변화**시킵니다.
    * 마우스를 올렸을 때 변화하여야 하므로 가상 클래스 `:hover`를 사용합니다. 
    * &lt;ul&gt;의 padding-top에 transition-delay 값을 줘서 변화시키면, 높이의 변화와 목록의 움직임이 시간차로 발생하는 것처럼 보일 수 있습니다.
    ```css
        .site__list {
          transition: height 400ms , padding-top 400ms 400ms;
        }

        .site__list:hover {
          height: 10.0625rem;
          padding-top: 0.75rem;
        }
    ```

<br />
<br />

# *️⃣ 결과
![Mission 03 transition fin](https://github.com/kimInDa/home-work/assets/105577805/59c6701e-0437-462e-afe7-f90f840f6c6a)