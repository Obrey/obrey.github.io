---
created: 2024-01-04 16:17
updated: 2024-01-04 17:04
date: 2024-01-04
tags:
  - Hugo
  - theme
  - Github
  - GithubPages
  - Git
  - Website
aliases:
  - 휴고
  - 테마
  - 깃허브
  - 깃허브페이지
  - 깃
  - 웹사이트
MOC: "[[09. MOC/Develop MOC]]"
title: css 수정하기
weight: "6"
---

---

### 연결 문서
- 

### 메모
`custom.css` 파일이 필요한 경우, 스타터 키트에는 없으므로 직접 생성해야 합니다.
기본 폴더에 `assets/css` 경로로 폴더를 생성하고, css 폴더에 `custom.css` 파일을 생성합니다. 저는 터미널에서 `touch custom.css` 명령어를 사용하여 생성하였습니다.

`custom.css`에서 다음과 같이 수정할 수 있습니다.
```css.custom
:root {
    --default-font: 'NanumSquareNeo-Variable', sans-serif;
    --body-font: 'Pretendard-Regular', sans-serif;
    --code-font: 'Roboto', sans-serif;
    --japanese-font: 'M PLUS 1p', sans-serif;
    --handwriting-font: 'omyu_pretty', sans-serif;
  }

html {
    font-family: var(--body-font);
}

.content {
    font-family: var(--body-font);
}

h1, h2, h3, h4, h5, h6 {
    font-family: var(--default-font), var(--japanese-font), sans-serif ;
    font-weight: bold ;
}

h1 {
    font-size: 1.7em !important;
}

h2 {
    font-size: 1.6em !important;
}

h3 {
    font-size: 1.5em !important;
}

h4 {
    font-size: 1.4em !important;
}

h5 {
    font-size: 1.3em !important;
}

h6 {
    font-size: 1.2em !important;
}
```
저는 폰트를 임포트하고, 루트 디렉토리를 생성하여 적당히 수정하였습니다. 이 테마는 디자인적으로 너무나 마음에 들어서 수정할 것은 폰트밖에 없었습니다. 테마 개발자분 감사합니다!

### 참조
- https://imfing.github.io/hextra/docs/advanced/customization/