#기본구조

    <html>
    <head>
      <title> 제목 </title>
    </head>
    <body>
      내용
    </body>
    </html>

-----------------

#주석

    <!-- 주석내용 -->

---------------------

#body 태그에 사용되는 속성

##bgcolor

    <body bgcolor="pink">

color의 이름을 직접 적을수도 있고,

    <body bgcolor="#ffdede">

16진수형태의 rgb값을 사용할 수도 있다.

##background
배경을 색이 아니라 이미지로 할 수도 있다.

    <body background="파일경로명">

절대경로나 상대경로 모두 사용할 수 있고, 아래처럼 url을 사용해도 된다.

    <body background="url">

---------------------

#br 태그
줄바꿈.

---------------------

#p 태그
paragraph

##align

    <p align="정렬방식">텍스트</p>

정렬방식 : left(default), right, center

---------------------

#br과 p의 차이
br은 단순히 줄바꿈을 위한 태그이므로 여러 번 적으면 그 횟수만큼 줄바꿈이 이루어지지만, p를 여러 번 적으면 이미 하나의 문단을 구성하였다고 인식하기 때문에 나머지 p에 대해서는 무시해버린다.

---------------------

#div 태그
한 행 모두가 그 영역에 해당된다.

    <div style="background-color:red">텍스트</div>

---------------------

#span 태그
글자 크기만큼이 그 영역에 해당된다.

    <span style="background-color:red">텍스트</span>

---------------------

#&nbsp
스페이스

---------------------

#pre 태그
원하는 곳에 지정한 문장을 배치하고 싶을 때. html문서에서 쓴 그대로 문장이 쓰여진다. pre 태그 안에서 다른 태그는 사용하지 않아야 한다. *html5에서는 지원하지 않는다.*

---------------------

#hr 태그
구분선. horizontal ruler

##hr 태그 속성

- width : 너비(비율, 픽셀수)
- size : 선의 두께(픽셀수)
- align : left, right, center
- noshade : 음영효과 없이
- color : 선의 색상

---------------------

#hn 태그
headline. 제목. 6단계. h1이 크기가 제일 크고, h6이 제일 크기가 작다.

##align
left, right, center, justify(여러 줄일때, 끝을 맞춰줌)


----------------------------

#font 태그
##face
글꼴.

    <font face="돋움">글꼴이 돋움체</font>

##size
글자의 크기(1단계~7단계). 7이 글자크기가 제일 크다.

    <font size="5">글자크기가 5</font>

크기를 상대적으로도 지정할 수 있다.

    <font size="+3">글자크기를 +3</font><br>
    <font size="-1">글자크기를 -1</font><br>

##color
글자의 색상.

    <font color="red">글자색상이 빨간색</font><br>
    <font color="#ffdede"글자색상이 핑크색</font><br>

----------------------------

#basefont 태그
html문서의 기본 글자 크기를 지정. 종료태그 없음. html의 기본 글씨 크기는 4이다. html5에서는 지원 안함.

    <basefont size="6">

----------------------------

#글자에 장식효과를 주는 태그

##b 태그

    <b>...</b>
    <strong>...</strong>

글자를 굵게

##i 태그

    <i>...</i>
    <em>...</em>

이탤릭체

##u 태그

    <u>...</u>

밑줄

##sub 태그

    <sub>...</sub>

아래첨자

##sup 태그

    <sup>...</sup>

위첨자

##big 태그

    <big>...</big>

좀 더 크게

##small 태그

    <small>...</small>

좀 더 작게

##s 태그

    <s>...</s>
    <strike>...</strike>

취소선

##tt 태그

    <tt>...</tt>

타자기 체. 가로 세로 비율이 고정되어 있는 글꼴.

--------------

#blockquote 태그
다른 글을 인용하는 경우 사용하는 태그.

-------------

#address 태그
주소나 연락처를 기술할 때 사용하는 태그. 이탤릭체로 표현된다.

--------------

#목록 태그

- ul 태그 : unordered list
- ol 태그 : ordered list
- dl 태그 : definition list

##li 태그
실제 list내용을 담는 태그. li 태그는 br 태그를 내포하고 있다.

##ul 태그
unordered list

###type
disc(검은원. default), circle(흰 원), square(사각형)

    <ul type="square">
      <li>고양이</li>
      <li>강아지</li>
      <li>토끼</li>
    </ul>

##ol 태그
ordered list

###type
- 1 : 숫자(default). 1, 2, 3, ...
- a : 영어 소문자. a, b, c, ...
- A : 영어 대문자. A, B, C, ...
- i : 소문자 로마 숫자. ⅰ, ⅱ, ⅲ, ...
- I : 대문자 로마 숫자. Ⅰ, Ⅱ, Ⅲ, ...
- disc : 검은 원
- circle : 흰 원
- square : 사각형

###start
type이 1, i, I인 경우 시작할 숫자를 지정할 수 있다. type이 a나 A인 경우에 start="2"하면, b나 B부터 시작한다.

    <ol type="I" start="2">
      <li>고양이</li>
      <li>강아지</li>
      <li>토끼</li>
    </ol>

결과로,

    ⅱ. 고양이
    ⅲ. 강아지
    ⅳ. 토끼

와 같이 출력된다.

##dl 태그
definition list

- lh 태그 : list head
- dt 태그 : definition title. <br>내포.
- dd 태그 : definition data. <br>내포.

    <dl compact>
      <dt>용어의 제목</dt>
      <dd>용어의 의미</dd>
    </dl>

용어의 제목 옆에 용어의 설명이 바로 나오도록 줄바꿈을 안시키려면, compact 속성을 사용한다.

--------------------

#img 태그

##img 속성

- src : 이미지 파일 경로
- align : 이미지 정렬 방식(top/middle/bottom, left/right)
- alt : 이미지 설명 문장
- title : 이미지의 title
- width : 폭
- height : 높이
- border : 이미지 두께
- hspace : 좌우여백
- vspace : 상하여백

align의 top/middle/bottom은 글자가 그림의 어느위치에 놓일 것인가인데, left/right는 그림이 왼쪽이냐 오른쪽이냐를 지정하는 것이다.

width나 height 중 하나만 지정하면 나머지는 그 비율에 맞게 되지만, 둘다 지정한 경우는 비율을 생각안하고 그 사이즈가 된다.

------------------

#하이퍼링크
하이퍼링크(hyperlink) : 연결된 개체

##a 태그 속성

- href : hyper reference의 약자. 하이퍼링크 연결로 이동하고자 하는 곳의 위치.
- name : 하이퍼링크의 이름.
- target : url이 보여질 위치.
- title : 하이퍼링크에 대한 설명.

*target="_blank"* 라고 지정하면 새로운 페이지를 열고 그 페이지에서 링크로 이동한다.

##링크의 색상 지정

    <body link="색상" vlink="색상" alink="색상">
    ...
    </body>

link는 연결된 적이 없는 상태의 색상. vlink는 한번이라도 방문한 상태의 색상. alink는 마우스로 누르고 있는 상태의 색상.

-----------------

#table 태그

##table 태그 속성

- border : 그냥 table을 작성하면 테두리가 표시되지 않기 때문에, border 속성을 사용해야 한다.
- align : 테이블 정렬 방식(테이블 전체의 위치)
- width : 너비(숫자 or 퍼센트)
- height : 높이
- cellpadding : 셀 테두리와 내용 사이의 간격
- cellspacing : 셀과 셀 사이의 경계 간격
- background : 배경이미지
- bgcolor : 색상
- bordercolor : 테두리 색상(default는 회색)

    <table border="1">
    ...
    </table>

##caption 태그
테이블의 제목 표시.

    <caption align="top">...</caption>

테이블 위에 제목을 쓰려면 top을, 아래에 쓰려면 bottom으로 지정.

##tr 태그
table row.

##th 태그
table header. 굵은 글씨와 가운데 정렬

##td 태그
table data.
