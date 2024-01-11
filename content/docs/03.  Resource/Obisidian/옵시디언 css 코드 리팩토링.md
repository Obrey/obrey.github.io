---
created: 2023-10-27 15:54
updated: 2024-01-11 20:34
date: 2023-10-27
tags:
  - CSS
  - Obsidian
  - WebFont
  - CodeRefactoring
aliases:
  - 옵시디언
  - 웹폰트
  - 코드리팩토링
title: 옵시디언 css 코드 리팩토링
---
---

### 연결문서
- 

### 메모
```css
:root {
--default-font: 'NanumSquareNeo-Variable', sans-serif;
}

/*title*/
.inline-title {
    font-size: 1.6em;
    color: #a3be8c;
    font-family: 'NanumSquareNeo-Variable', sans-serif;
}

/* 행간 조절 */
.cm-contentContainer {
line-height: 1.5;
}

/* 문단 간 간격 조절 */
.markdown-source-view :is(.cm-line + .cm-line) {
padding-top: 0.7em;
}

/* Markdown and code font settings */
.markdown-source-view.mod-cm6 .cm-scroller,
.markdown-preview-view,
.cm-scroller {
text-align: left;
font-family: 'Gowun Dodum','Klee One';
}

.tag,
.cm-s-obsidian span.cm-tag-S,
.cm-s-obsidian span.cm-hashtag-begin,
.cm-s-obsidian span.cm-hashtag-end {
font-family: 'NanumSquareNeo-Variable', sans-serif;
}

strong,
.cm-s-obsidian span.cm-formatting-strong,
.cm-s-obsidian span.cm-strong,
i,
em,
span.cm-em {
font-family: 'Gowun Dodum', sans-serif;
}

.cm-s-obsidian span.cm-inline-code,
.cm-s-obsidian .HyperMD-codeblock  {
font-family: 'NanumSquareNeo-Variable', sans-serif;
}

.metadata-properties,
.metadata-properties *,
.metadata-add-button,
.metadata-properties-heading {
font-family: 'NanumSquareNeo-Variable', sans-serif;
}

/* Header styles */
.HyperMD-header-1, .markdown-rendered h1, .markdown-preview-view h1, .cm-header-1 {
    font-size: 1.6em;
    color: #a3be8c;
    font-family: 'NanumSquareNeo-Variable', sans-serif;
}

.HyperMD-header-2, .markdown-rendered h2, .markdown-preview-view h2, .cm-header-2 {
    font-size: 1.5em;
    color: #8fbcb7;
    font-family: 'NanumSquareNeo-Variable', sans-serif;
}

.HyperMD-header-3, .markdown-rendered h3, .markdown-preview-view h3, .cm-header-3 {
    font-size: 1.4em;
    color: #88c0d0;
    font-family: 'NanumSquareNeo-Variable', sans-serif;
}

.HyperMD-header-4, .markdown-rendered h4, .markdown-preview-view h4, .cm-header-4 {
    font-size: 1.3em;
    color: #BEAEE2;
    font-family: 'NanumSquareNeo-Variable', sans-serif;
}

.HyperMD-header-5, .markdown-rendered h5, .markdown-preview-view h5, .cm-header-5 {
    font-size: 1.2em;
    color: #F1C6E7;
    font-family: 'NanumSquareNeo-Variable', sans-serif;
}

.HyperMD-header-6, .markdown-rendered h6, .markdown-preview-view h6, .cm-header-6 {
    font-size: 1.1em;
    color: #F6ECBF;
    font-family: 'NanumSquareNeo-Variable', sans-serif;
}

/* 콜아웃 제목 */
.callout-title-inner{
  font-family: 'NanumSquareNeo-Variable', sans-serif;
   color: #81a1c1;
}

/* 콜아웃 아이콘 */
.callout-icon svg {
    stroke: #81a1c1;
}

/* 코드블럭 폰트 설정 */
.cm-hmd-codeblock {
font-family: 'ROBOTO', 'NanumSquareNeo-Variable', sans-serif;
}

```
이런식으로 각각으로 지정하는거에서


```css
:root {  
  --default-font: 'NanumSquareNeo-Variable', sans-serif;  
  --body-font: 'Gowun Dodum', sans-serif;  
  --code-font: 'Roboto', sans-serif;  
  --japanese-font: 'Klee One', sans-serif;  
}  
  
/*title*/  
.inline-title {  
    font-size: 1.6em;  
    color: #a3be8c;  
    font-family: var(--default-font);  
}  
  
/* 행간 조절 */.cm-contentContainer {  
line-height: 1.5;  
}  
  
/* 문단 간 간격 조절 */.markdown-source-view :is(.cm-line + .cm-line) {  
padding-top: 0.7em;  
}  
  
/* Markdown and code font settings */  
.markdown-source-view.mod-cm6 .cm-scroller,  
.markdown-preview-view,  
.cm-scroller {  
text-align: left;  
font-family: var(--body-font),var(--japanese-font);  
}  
  
.tag,  
.cm-s-obsidian span.cm-tag-S,  
.cm-s-obsidian span.cm-hashtag-begin,  
.cm-s-obsidian span.cm-hashtag-end {  
font-family: var(--default-font);  
}  
  
strong,  
.cm-s-obsidian span.cm-formatting-strong,  
.cm-s-obsidian span.cm-strong,  
i,  
em,  
span.cm-em {  
font-family: var(--body-font);  
}  
  
.cm-s-obsidian span.cm-inline-code,  
.cm-s-obsidian .HyperMD-codeblock  {  
font-family: var(--default-font);  
}  
  
.metadata-properties,  
.metadata-properties *,  
.metadata-add-button,  
.metadata-properties-heading {  
font-family: var(--default-font);  
}  
  
/* Header styles */  
.HyperMD-header-1, .markdown-rendered h1, .markdown-preview-view h1, .cm-header-1 {  
    font-size: 1.6em;  
    color: #a3be8c;  
    font-family: var(--default-font);  
}  
  
.HyperMD-header-2, .markdown-rendered h2, .markdown-preview-view h2, .cm-header-2 {  
    font-size: 1.5em;  
    color: #8fbcb7;  
    font-family: var(--default-font);  
}  
  
.HyperMD-header-3, .markdown-rendered h3, .markdown-preview-view h3, .cm-header-3 {  
    font-size: 1.4em;  
    color: #88c0d0;  
    font-family: var(--default-font);  
}  
  
.HyperMD-header-4, .markdown-rendered h4, .markdown-preview-view h4, .cm-header-4 {  
    font-size: 1.3em;  
    color: #BEAEE2;  
    font-family: var(--default-font);  
}  
  
.HyperMD-header-5, .markdown-rendered h5, .markdown-preview-view h5, .cm-header-5 {  
    font-size: 1.2em;  
    color: #F1C6E7;  
    font-family: var(--default-font);  
}  
  
.HyperMD-header-6, .markdown-rendered h6, .markdown-preview-view h6, .cm-header-6 {  
    font-size: 1.1em;  
    color: #F6ECBF;  
    font-family: var(--default-font);  
}  
  
/* 콜아웃 제목 */.callout-title-inner{  
  font-family: var(--default-font);  
   color: #81a1c1;  
}  
  
/* 콜아웃 아이콘 */.callout-icon svg {  
    stroke: #81a1c1;  
}  
  
/* 코드블럭 폰트 설정 */.cm-hmd-codeblock {  
font-family: var(--code-font), var(--default-font);  
}
```
변수 사용해서 수정이 쉽도록 변경함!

### 참조
- 