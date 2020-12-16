# HTML 

## 1) summary
- Hyper Text Markup Language 의 약자
- 웹 문서를 작성하는 마크업 언어
- 웹 페이지를 구성하는 언어
    - HTML : 화면의 레이아웃이나 텍스트
    - CSS : 화면의 색상, 크기 등의 스타일 (css-selector)
    - Javascrript : 화면의 클릭, 드래그 등등의 이벤트
- HTML 구성요소
    - Document
        - HTML 코드를 구성하고 있는 모든 문자열 코드
        - 페이지 전체를 의미, doctype
    - Element
        - 계층적 구조로 이루어짐
        - Document를 구성하고 있는 단위
        - 시작 Tag 와 끝 Tag 로 구성
    - Tag
        - Element 를 구성하는 단위
        - Tag 의 종류에 따라서 웹 서비스에서 사용되는 기능이 달라짐
        - 시작 Tag 에는 여러가지 속성값들이 있음
        - div, ul, li, a, p, span, img, table 등
    - Attribute
        - 시작태그에 태그의 속성을 설정하는 값
        - id, class : 엘리먼트를 선택하기 위한 목적으로 만들어진 속성값
            - id : 웹페이지 내에서 유일한 값, 보통 하나만 사용함
            - class : 페이지 내에서 같은 값 사용이 가능함. 엘리먼트내에서도 여러개 설정
        - 기타

## 2) tag 종류
### 2)-1 Head : 제목을 나타낼 때 사용
- h1 ~ h6 : fontsize
```
%%html
<h1>Python</h1>
<h2>HTML</h2>
<h3>Document</h3>
<h4>Element</h4>
<h5>Tag</h5>
<h6>Attribute</h6>

==========<print>===========

Python
HTML
Document
Element
Tag
Attribute
```
### 2)-2 p : 한줄의 문자열을 출력하기 위한 태그
```
%%html
<p>Summary of HTML</p>
<p>With Python</p>
<p>메리크리스마스</p>

==========<print>===========

Summary of HTML

With Python

메리크리스마스
```

### 2)-3 span : 한블럭의 문자열을 출력
- span 안에 있는 문자열이 한블럭으로 나온다.
```
%%html
<span>검찰총장의 징계가 확정되었습니다.</span>
<span>2개월간 면직처분이 내려질 예정입니다.</span>
<span>추미애 장관의 징계결정에 대한 문재인 대통령의 재가가 남았습니다.</span>

==========<print>===========

검찰총장의 징계가 확정되었습니다. 2개월간 면직처분이 내려질 예정입니다. 추미애 장관의 징계결정에 대한 문재인 대통령의 재가가 남았습니다.
```

### 2)-4 div : 레이아웃을 나타내는 태그
```
%%html
<div>
    <p>Summary of HTML</p>
    <p>With Python</p>
</div>
<div>
    <p>권력기관 개혁입법 3법 국회통과</p>
</div>

==========<print>===========

Summary of HTML

With Python
권력기관 개혁입법 3법 국회통과
```

### 2)-5 table : 엘리먼트, 로우와 컬럼이 있는 테이블 모양을 나타낼때 사용되는 태그

```
%%html
<table>
    <thead>
        <tr>
            <tr>ghm.co </tr>
            <tr>tipidea </tr>
            <tr>eatsue </tr>
            <tr>blog </tr>
            <tr>commerce </tr>
            <tr>contact </tr>
        </tr>
    </thead>
        <caption>광화문컴퍼니</caption>
        <today>
            <tr>
            <caption>python</caption>
            </tr>
        </today>
</table>

==========<print>===========

ghm.co tipidea eatsue blog commerce contact
광화
문컴
퍼니

python
```

### 2)-6 li :

```
%%html
<ul>
    <li>data 1</li>
    <li>data 2</li>
    <li>data 3</li>
</ul>

==========<print>===========

- data 1
- data 2
- data 3
```

```
### 2)-7 a : 링크를 출력하는 태그
- 출력된 이름을 누르면 해당 url 로 연결된다.
```
%%html
<a href="https://canary---yellow.com/" target="_blank">canay_yellow</a>

==========<print>===========

canay_yellow
```

### 2)-8 img 관련 태그
- src url : 웹사이트의 이미지의 주소를 저장하는 태그
- iframe : 외부 url 링크의 페이지를 보여주기 위한 태그
    - 설정된 url 로 가져와야한다.
- virgil abloh 의 홈페이지 배경 가져오기
```
%%html
<img style="width:400px;" src="https://d3uqg2ap1kpnl9.cloudfront.net/wp-content/uploads/2020/07/06103047/bg-canary-yellow.jpg">
```
![bg-canary-yellow](./images/bg-canary-yellow.jpg)

```
%%html
<iframe src="https://d3uqg2ap1kpnl9.cloudfront.net/wp-content/uploads/2020/07/06103047/bg-canary-yellow.jpg" width="100%" height="300x"></iframe>
```
![bg-canary-yellow_big](./images/bg-canary-yellow_big.jpg)

```
# 3. CSS Selector
- HTML 의 Element 에 CSS 스타일을 적용시킬때, element 를 선택하기 위한 방법

## 1) Element 를 선택하는 방법
    - data 1 엘리먼트 선택
        - Tag 이름 사용 : div
        - id 값 사용 : #wrap
        - class 값 사용 : .dss
    - data 2엘리먼트 선택
        - id 값 사용 : #txt
        - class 값 사용 : .no1 또는 .dss-txt -> data 2,3 이 같이 선택된다.
    - data 3 엘리먼트 선택 :
        - class 값 사용 : .no2 또는 .dss-txt -> data 2,3 이 같이 선택된다.
        - 속성값 사용 : [val="d3"]
    - data 4 엘리먼트 선택
        - id 값 사용 : #da4
        - 속성값 사용 : [val="d4"], [id="da4"]
```
%%html
<div id="wrap" class="dss">data 1</div>
<p id="txt" class="dss-txt no1">data 2</p>
<span class="dss-txt no2" val="d3">data 3</span>
<span id="da4" val="d4">data 4</span>
<span class="no5">data 5</span>
```

## 2) Element 선택하는 방법 2
- not selector : 선택된 엘리먼트에서 특정조건의 엘리먼트를 제거해서 선택
    - data 2 엘리먼트만 제외하고 ds 클래스 선택 : .ds:not(.dss2)
- nth-child : n 번째의 엘리먼트를 선택
    - data 3 엘리먼트를 선택 : .ds:ntn-child(3)
    - 클래스 ds 에서 3 번쨰 엘리먼트를 선택

## 3) Element 선택하는 방법 3
- 계층구조로 엘리먼트 선택
    - 바로 아래 단계, inner 1 엘리먼트 선택 : .wrap-1 > h5
    - 모든 하위 엘리먼트 전체 선택, inner 1, inner 2 선택 : .wrap-1 h5
```
%%html
<div class="wrap-1">
    <h5>inner 1</h5>
    <div class="wrap-2">
        <h5>inner 2</h5>
    </div>
</div>
```
