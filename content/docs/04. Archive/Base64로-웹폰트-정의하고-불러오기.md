---
created: 2023-11-03 13:41
updated: 2024-01-11 20:35
date: 2023-11-03
tags:
  - CSS
  - Font
  - WebFont
  - Base64
aliases:
  - 폰트
  - 웹폰트
  - 글꼴
title: Base64로-웹폰트-정의하고-불러오기
---
---

### 연결문서
- 

### 메모
웹폰트를 Base64로 정의하고 불러오는 방법은 웹페이지의 로딩 속도를 향상시키고, 서버 요청을 줄이는 등의 장점이 있습니다.

1. 먼저, 원하는 폰트 파일을 Base64로 인코딩해야 합니다. 이를 위해 [Base64 인코더 사이트](https://www.giftofspeed.com/base64-encoder/)를 이용할 수 있습니다.
2. 해당 사이트에서 폰트 파일을 업로드합니다.
3. 업로드한 폰트 파일의 확장명에 따라 url 경로를 작성합니다. 예를 들어, ttf 파일의 경우 다음과 같이 작성할 수 있습니다:

```css
@font-face{
    font-family:'yourfontname'; 
    src: url(data:application/font-ttf;charset=utf-8;base64,YOUR BASE64 STRING HERE) format('truetype');
}
```

4. 폰트 확장명에 따른 @font-face 코드는 다음과 같습니다:

- OpenType Fonts:

```css
@font-face{
    font-family:'yourfontname'; 
    src: url(data:font/opentype;charset=utf-8;base64,YOUR BASE64 STRING HERE);
}
```

- WOFF Fonts:

```css
@font-face{
    font-family:'yourfontname'; 
    src: url(data:application/font-woff;charset=utf-8;base64,YOUR BASE64 STRING HERE) format(woff);
}
```

- WOFF2 Fonts:

```css
@font-face{
    font-family:'yourfontname'; 
    src: url(data:application/font-woff2;charset=utf-8;base64,YOUR BASE64 STRING HERE) format(woff2);
}
```

- TTF Fonts:

```css
@font-face{
    font-family:'yourfontname'; 
    src: url(data:application/font-ttf;charset=utf-8;base64,YOUR BASE64 STRING HERE) format('truetype');
}
```

이렇게 Base64로 웹폰트를 정의하고 불러오는 방법을 사용하면, 웹페이지의 로딩 속도를 향상시키고 서버 요청을 줄일 수 있습니다. 이는 웹페이지의 성능을 향상시키는 데 크게 기여합니다.

### 참조
- 