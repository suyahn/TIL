#CSS (Cascading Style Sheets)

- head 태그 사이에 삽입
- <style>로 시작하고 </style>로 끝난다.

#기본 형식

    selector {속성: 값}

selector는 스타일 적용 대상. 주로 tag들.

예를 들어 h1태그에서 색상을 red로 하고 싶다면,

    h1 { color: red }

위와 같이 하면 된다.

속성이 여러 개라면 세미콜론으로 구분한다.

예를 들어, p 태그를 18픽셀의 초록색 굴림체로 지정하려면,

    p {
      font-size: 18px;
      font-family: 굴림;
      color: green;
    }

#embedding, link, inline

- embedding은 head태그에 스타일설정을 삽입.
- link는 외부 css파일에 존재하는 스타일시트 파일을 html에 삽입하는 방식
- inline은 html문서의 태그에서 직접 스타일을 설정하는 방식.

아래처럼 쓰는 건 inline방식이다.

    <h1 style="font-size: 10px; background: yellow;">대박</h1>

만약 embedding방식과 inline방식 두가지가 섞여 있다면, inline방식이 우선순위가 높다.
