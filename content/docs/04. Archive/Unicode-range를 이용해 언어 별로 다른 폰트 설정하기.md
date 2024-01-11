---
created: 2023-10-25 21:25
updated: 2024-01-11 20:35
Date: 2023-10-25
tags:
  - Font
  - Unicode
  - UnicodeRange
  - CSS
  - WebFont
  - Obsidian
aliases:
  - 폰트
  - 유니코드
  - 웹폰트
  - 옵시디언
MOC: "[[../../09. MOC/Develop MOC]]"
title: Unicode-range를 이용해 언어 별로 다른 폰트 설정하기
---
---

### 연결문서
- 

### 메모
#### Unicode란 무엇인가?
Unicode는 전 세계의 모든 문자를 컴퓨터에서 일관되게 표현하고 다루기 위한 국제 표준입니다. 각 문자나 기호는 고유의 코드 포인트를 가지며, 이 코드 포인트는 U+ 뒤에 4~6자리의 16진수로 표현됩니다.

#### Unicode-range란 무엇인가?
unicode-range는 CSS @font-face 규칙의 속성 중 하나로, 웹 폰트가 적용되는 문자의 범위를 지정합니다. 이 유니코드를 사용하여 한글을 작성할 때에는 한글 폰트, 영어를 작성할 때에는 영어 폰트로 작성을 할 수 있습니다. 다음은 언어에 따른 유니코드 범위입니다.

|**언어**|**유니코드 범위**|
|---|---|
|영어 대소문자|U+0041-005A, U+0061-007A|
|일본어 히라가나|U+3040–U+309F|
|일본어 카타카나|U+30A0–U+30FF|
|한국어|U+AC00–U+D7AF|
|중국어|U+4E00–U+9FFF|

일반적으로 이렇게 사용하지만 더 자세한 정보는 다음의 사이트에서 알 수 있습니다.

#### Unicode-range를 이용해 언어별로 다른 폰트 설정하기
옵시디언에서는 사용자 정의 CSS를 통해 언어별로 다른 폰트를 설정할 수 있습니다. 이를 위해선 먼저 옵시디언의 설정에서 “사용자 정의 CSS 스니펫” 옵션을 활성화해야 합니다. 그런 다음, snipet 폴더에 CSS 파일을 생성합니다. 이미 있다면 그 파일에서 진행해도 상관없습니다. CSS 파일에서 @font-face 규칙을 사용하여 원하는 언어의 유니코드 범위에 대한 웹 폰트를 정의합니다.

예를 들어, 현재 자신은 Noto Serif 폰트를 적용시킨 상태에서 영어를 작성하는 경우에 Open Sans 폰트를 적용하고 싶다면,

```javascript
@font-face {
  font-family: 'Noto Serif';
  src: url('URL to Noto Serit font file');
  unicode-range: U+AC00–U+D7AF;
}

@font-face {
  font-family: 'Noto Serif';
  src: url('URL to Open Sans English font file');
  unicode-range: U+0041-005A, U+0061-007A;
}
```

이런 식으로 작성합니다. Noto Serif 폰트로 지정된 폰트는 영어로 작성하면 자연스럽게 Open Sans 폰트로 쓰입니다. 최종적으로 영어, 일본어, 한국어 유니코드를 이용해 작성했으며 폰트가 변경된 것을 확인했습니다.

|언어|폰트 확인|
|---|---|
|영어|Hello World|
|일본어 히라가나| ひらがな|
|일본어 카타카나|カタカナ|
|한국어|안녕하세요|

![폰트 변경 확인](https://i.imgur.com/NzjzyM2.png)

#### 코드 공유

```CSS
/* 한국어 */
@font-face {
  font-family: "Noto Serif";
  font-weight: 400;
  font-style: normal;
  src:url(https://cdn.jsdelivr.net/npm/noto-serif-kr@20.0.0/noto_serif_kr_regular/3Jn7SDn90Gmq2mr3blnHaTZXduUBwuF9Wxop-KlAZIoTrf6uFZh_9Q.88.woff2) format("woff2");
  unicode-range: U+AC00-D7AF;
}

/* 영어 오픈산스 */
@font-face {
  font-family: "Noto Serif";
  font-weight: 400;
  font-style: normal;
  src: url("https://www.eea.europa.eu/templates/v2/fonts/GoogleFonts-OpenSans-Regular2-v15.woff2") format('woff2');
  unicode-range: U+0041-005A, U+0061-007A;
}

/* 일본어 노토산스 jp */
@font-face {
  font-family: "Noto Serif";
  font-weight: 400;
  font-style: normal;
  src: url('https://cdn.jsdelivr.net/npm/typeface-notosans-jp@1.0.1/NotoSansJP-Regular.woff2') format("woff2");
     unicode-range: U+4E00–U+9FBF, U+3040–U+309F ;
}
```

#### 마치며
원래 구글 폰트의 주소로 하면 쉽게 될 거라 생각했습니다. 제 실력이 부족해서인지 font-face는 구글 웹폰트의 import가 안 먹혔습니다. 어쩔 수 없이 로컬 폰트를 저장해야 하는데 obsidian에서의 로컬 폰트의 경로 지정이 어려워 결국 다른 폰트 링크를 찾아 성공시켰습니다. 테스트용으로 급하게 Noto sans JP 폰트를 가져왔는데 여러 폰트를 보고 바꿀지 결정해야겠습니다.

### 참조
- https://cdn.jsdelivr.net/npm/@expo-google-fonts/noto-sans-kr@latest/
- https://symbl.cc/kr/