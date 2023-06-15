🦁 [ 멋사 프론트엔드 스쿨 6기 과제 ]

❖ Mission 05.sprite 코드 리뷰 ❖

<br />
<br />

# *️⃣ HTML Markup image

![Mission 05 sprite markup](https://github.com/kimInDa/home-work/assets/105577805/587e4be4-1416-43f1-beac-e9762c1b9ed2)



<br />
<br />

# *️⃣ 코드 리뷰
## ❖ HTML 마크업 순서
1. 가장 바깥은 **&lt;section&gt;** 요소로 감쌉니다.
  
2. **&lt;section&gt;** 의 내부에 영역의 제목인 **&lt;h2&gt;** 요소를 가장 먼저 마크업 하여 해당 영역이 어떤 영역인지 알려줍니다. 
   * 제목의 **'사이트'** 는 다른 색상을 스타일링해야 하므로 **&lt;span&gt;** 요소로 감쌉니다.

3. 그 다음으로는 영역의 주요 내용인 인기 사이트 순위를 마크업 합니다. 순서가 있는 목록이므로 **&lt;ol&gt;** 과 **&lt;li&gt;** 로 마크업합니다
   
   * **&lt;li&gt;** 는 자식요소로 **&lt;a&gt;** 를 갖습니다.
   * **&lt;a&gt;** 는 순위의 각 사이트 이름을 클릭할 시 해당 사이트로 이동하는 기능을 제공합니다.

4. 추가적인 정보를 제공하는 **+ 더보기** 는 가장 마지막에 둡니다. **+ 더보기** 를 클릭했을 때 인기 사이트에 대한 정보를 열람할 수 있는 페이지로 이동해야 하므로 **&lt;a&gt;** 요소를 사용합니다.
   
  <br />

## ❖ CSS 스타일링
### ✢ **&lt;a&gt;** 요소 에이전트 스타일링 초기화
* **&lt;a&gt;** 요소의 에이전트 스타일링을 초기화 하는 클래스를 만들어서 **+더보기**와 순위 목록의 **&lt;a&gt;** 에 부여합니다.
 
  ```CSS
  .favorite-link {
    text-decoration: none;
    color: inherit;
  }
  ```
<br />

### ✢ **+더보기** 위치 이동
* 가장 마지막에 마크업한 **+더보기** 를 예제의 위치로 옮기기 위하여 ``position`` 속성을 이용합니다.
* **+더보기** 의 부모 요소인 **&lt;section&gt;** 에 ``position:relative`` 를 부여하고 **+더보기** 에는 ``absolute`` 를 부여합니다.  
* **+더보기** 를 **&lt;section&gt;** 의 padding을 고려하여 ``top: 12px``, ``right 12px`` 의 위치로 이동시킵니다.
  
  ```CSS
  .favorite {
    box-sizing: border-box;
    padding: 12px;
    position: relative;
  }
  .favorite-more {
    position: absolute;
    top: 12px;
    right: 12px;
  }
  ```
<br />


### ✢ **&lt;ol&gt;** 숫자 스타일링
* ``list-style:none`` 을 사용해서 **&lt;ol&gt;** 의 기본 숫자를 지웁니다.
  
  ```CSS
  .favorite-list {
    list-style: none;
  }
  ```

* **&lt;li&gt;** 의 순서에 따라 숫자를 표현하기 위해 ``counter-increment`` 속성을 사용합니다.
* 갯수를 셀 **&lt;li&gt;** 에 ``counter-increment`` 속성을 적용하면 number에 **&lt;li&gt;** 의 갯수가 담깁니다. 
* 가상 요소 ``::before``로  **&lt;li&gt;** 의 앞에 번호를 구현하기 위해, ``::before``의 ``content`` 값으로 ``counter()``  함수를 사용합니다.
* 생성된 번호는 ``inline`` 상태이므로 형제 요소와 가로 정렬을 유지하면서 width, height 값을 가질 수 있도록 ``display: inline-block;`` 속성을 부여합니다.
* ``text-align: center;`` 속성으로 번호가 자신의 박스 안에서 가로 가운데 정렬이 되도록 합니다.
* ``line-heihgt`` 값을 ``height`` 값과 동일하게 주어 번호가 자신의 박스 안에서 세로 가운데 정렬이 되도록 합니다.
  
  ```CSS
  .favorite-rank {
    counter-increment: number;
  }
  .favorite-rank::before {
    content: counter(number);
    display: inline-block;
    width: 16px;
    height: 16px;
    color: #fff;
    background: #A3A3A3;
    border-radius: 5px;
    text-align: center;
    line-height: 16px;
    margin-right: 4px;
  }
  ```
  <br />

### ✢ sprite 기법으로 순위 변동 이미지 넣기

* 순위 변동 이미지를 **&lt;li&gt;** 요소의 배경 이미지로 넣기 위해 모든 **&lt;li&gt;** 요소에 ``class="sprite"`` 를 선언합니다.
  
* ``.sprite`` 클래스 선택자에 배경 이미지로 순위 변동 이미지를 불러옵니다. 에이전트 스타일로 인해 배경이미지가 반복 되므로 ``no-repeat`` 도 함께 부여합니다.
*  공통으로 선택자를 지정하여 배경이미지를 불러올경우 이미지를 한 번만 불러 오면 되므로 성능 개선에 도움 됩니다.
*  각 **&lt;li&gt;** 별로 필요한 이미지는 ``background-position``으로 이미지의 위치를 조정하여 구현합니다. 이를 위해 각 **&lt;li&gt;** 마다 개별 클래스를 부여합니다.
    ```CSS
      .sprite {
        background: url(./rank.png) no-repeat;
      }
      .spriteW3C {
        background-position: right -5%;
      }
      .spriteWeb {
        background-position: right 105%;
      }
      .spriteCSS {
        background-position: right center;
      }
      .spriteMDN {
        background-position: right -5%;
      }
    ```

<br />
<br />

# *️⃣ 결과
![Mission 05 sprite fin](https://github.com/kimInDa/home-work/assets/105577805/8cfd8f9f-8e53-49fd-9a81-914793836550)