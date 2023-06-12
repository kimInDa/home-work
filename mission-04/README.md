🦁 [ 멋사 프론트엔드 스쿨 6기 과제 ]

❖ Mission 04.Grid 코드 리뷰 ❖

<br />
<br />

# *️⃣ HTML Markup image

![Mission 04 grid markup](https://github.com/kimInDa/home-work/assets/105577805/155cefe1-c862-4cc3-95dd-25d092a8484d)

<br />
<br />

# *️⃣ 코드 리뷰
## ❖ Grid 레이아웃
### ✢ coulmn 나누기
* 예제에 따르면 **전체 영역**의 width는 `380px`입니다. 
* 내부 요소인 **새소식**, **더보기** 의 width는 `각각 37px`입니다.
* 이에 **coulumn**을 `37px 10개`와 `gap 1px`로 나눈다 가정하고 계산해봅니다.
  
  ![2023-06-12_23-54-13](https://github.com/kimInDa/home-work/assets/105577805/7203d650-4c5a-47b2-8ab8-c4fc2d5af46f)
* 예제에서 **이미지 영역**인 **&lt;figure&gt;** 의 width는` 112px`입니다. ` 37px * 3 = 111px`에 `gap 1px * 2 = 2px`를 포함한다면 `113px`로 예제의 width와 유사한 크기를 가집니다. 
* 예제 오른쪽 하단 **텍스트 영역** 의 width는 `왼쪽 margin 17px`을 포함하여 `268px`입니다. `37px * 7 = 259px`에 `gap 1px * 7 = 7px`을 더하면 `266px`로 예제와 유사한 크기를 가집니다.
* 따라서 전체 영역을 `grid-column 37px`짜리` 10개`로 나누고 `gap 1px`을 지정합니다. 
  
* gird-row는 각 행마다 콘텐츠의 크기에 따라 자연스럽게 height을 가질 수 있도록 auto 값을 줍니다.
  ```CSS
  .news {
  width: 380px;
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: auto;
  gap: 1px;
  }
  ```

<br />

### ✢ 요소 배치하기
  ![2023-06-13_00-06-15](https://github.com/kimInDa/home-work/assets/105577805/9c957c3a-b89e-4066-87fc-164a55068bd3)
* **새소식** 과 **더보기** 는 column과 row 모두 1개의 영역을 가집니다.
  
* **구분선**은 row 1개, column 10개의 영역을 가집니다.
  
* 오른쪽 하단 **콘텐츠의 제목, 날짜, 내용**은 모두 각각 row 1개, column 7개씩의 영역을 가집니다. 세 요소의 왼쪽에 margin을 주어서 **이미지 영역**과의 거리를 조정합니다.
  ``` CSS
    .news__contentTitle,
    .news__contentDate,
    .news__contentText  {
      margin-left: 16px;
    }
  ```
  
* **이미지 영역**인 **&lt;figure&gt;** 는 콘텐츠 사이즈에 맞도록 column 3개를 가집니다. 오른쪽 텍스트 영역으로 인해 생겨난 row 3개도 가집니다.
  


<br />
<br />

## ❖ 제목

* 예제 영역에 대한 제목 **'새소식'은 &lt;h2&gt;로 마크업** 합니다.
* 내부 콘텐츠의 제목 **'W3C 사이트가 리뉴얼 되었습니다."** 는 보다 작은 레벨의 **&lt;h3&gt;로 마크업** 합니다.
  
    ```html
      <!-- 예제 영역의 제목 -->
        <h2 class="news__title">새소식</h2>

      <!-- 콘텐츠의 제목 -->
        <h3 class="news__contentTitle">W3C 사이트가 리뉴얼 되었습니다.</h3>
    ```

<br />
<br />

## ❖ **+** 더보기
* 더보기를 누르면 새소식 페이지로 이동할 수 있도록 **&lt;a&gt;** 로 마크업 합니다.

* **&lt;a&gt;** 에는 `text-decoration: none;`을 부여하여 에이전트 스타일을 없앤 뒤에 예제에 따른 스타일링을 합니다.
  
* 더보기의 + 플러스 기호는 가상 클래스 `::before`의 content로 이미지를 넣어줍니다. 
  
* 플러스 기호의 위치는 **position**을 이용하여 조정하여 줍니다. **&lt;a&gt;** 에 `position:relative` 를,  **&lt;a&gt;의 ::before** 에는 `position:absolute;`를 사용하여 플러스 기호가 &lt;a&gt;를 기준으로 위치가 조정되도록 합니다.

  ``` CSS
  .news__more {
  position: relative;
  color: inherit;
  text-decoration: none;
  }
  .news__more::before {
  content: url(./plus-icon.png);
  position: absolute;
  right: 41px;
  }
  ```
<br />
<br />

## ❖ 구분선
* 구분선은 **&lt;hr&gt;** 로 마크업 합니다.
* `border-style: none;`과 `border-width: 0;`으로 에이전트 스타일을 없앱니다.
* height 값으로 예제에 지정된 높이를 주고 background로 그라데이션을 넣어 스타일링 해줍니다.
* 예제에 따라 margin 값으로 위쪽과 아래쪽 요소와의 공간을 만들어 줍니다.
  
  ```CSS
  .news--line {
    height: 1px;
    background: linear-gradient(90deg, #A9A9A9 -1.32%, #FFFFFF 100%);
    margin-top: 12px;
    margin-bottom: 24px;
    border-style: none;
    border-width: 0;
    grid-area: 2 / 1 / 3 / 8;
  }
  ```

<br />
<br />

# *️⃣ 결과
![Mission 04 grid fin](https://github.com/kimInDa/home-work/assets/105577805/ddc46564-8473-4817-a97a-98b9d13e114e)
