---
created: 2024-01-04 15:43
updated: 2024-01-04 20:36
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
title: yaml섹션 수정하기
weight: "5"
---
---

### 연결문서
- 

### 메모
`yaml` 확장자로 된 파일들을 수정해야 합니다. 폴더에서 `yaml`을 검색해서 나오는 파일들은 모두 열어서 수정해보세요.

#### hugo.yaml
##### 타이틀 수정하기
```
# Hugo configuration file
title: 타이틀 수정
```

##### navbar 메뉴 변경하기
```yaml
menu:
  main:
    - name: Documentation
      pageRef: /docs
      weight: 1
    - name: Blog
      pageRef: /blog
      weight: 2
    - name: About
      pageRef: /about
      weight: 3
    - name: Search
      weight: 4
      params:
        type: search
    - name: GitHub
      weight: 5
      url: "https://github.com/imfing/hextra"
      params:
        icon: github
```
이렇게 작성되어있는 항목이 있는데 이 부분은 

![](https://i.imgur.com/cBoEguc.png)
테마 상단의 이쪽을 담당합니다. 

```
  main:
    - name: Documentation
      pageRef: /docs
      weight: 1
```
위 코드를 보면, Documentation의 페이지 주소는 `/docs` (content폴더 내의 docs 폴더를 의미합니다.)이며, `weight`는 1로 가장 앞에 나오는 것을 알 수 있습니다. 위 바의 `Documentation`을 누르면 실제로 `docs/`페이지로 이동하는 것을 확인할 수 있습니다.

```
    - name: GitHub
      weight: 5
      url: "https://github.com/imfing/hextra"
      params:
        icon: github
```
이처럼 아이콘과 주소를 통해 링크 이동도 가능합니다. 

##### 로고 입력하기
```yaml
params:
  navbar:
    displayTitle: true
    displayLogo: true
    logo:
      path: images/logo.svg
      dark: images/logo-dark.svg
      link: /
      width: 40
      height: 20
```
이렇게 로고 입력도 가능합니다.

##### 다국어 지원 설정하기
```
defaultContentLanguage: kr
languages:
  kr:
    languageName: 한국어
    weight: 1
    title: 근청석
  en:
    languageName: English
    languageCode: en
    weight: 2
    title: Iolite
```
이렇게 하면 다국어도 지원 가능합니다. 디폴트로 설정된 언어는 따로 설정을 하지 않고 시행하면 바로 보입니다. 하지만 디폴트가 설정되 지 않은 , `en`이 설정된 파일은 `파일명_en.md`파일만을 인식합니다. 예를들어 프랑스어는 `fr`을 붙여야겠죠? 자세한 정보는 헥스트라에도 존재합니다. 

#### config.yaml
##### 구글 애널리틱스
```
services:
  googleAnalytics:
    ID: G-xxxxxxxxxx
```
이처럼 구글 애널리틱스에 등록이 가능합니다.

#### deploy, pages
`dploy.yaml`, `pages.yaml`의 baseURL을 자신의 주소로 만들어주세요.
기본적으로, `https://USER-NAME/github.io/REPO-NAME`으로 설정하면 됩니다.

### 참조
- https://imfing.github.io/hextra/docs/guide/configuration/
- https://imfing.github.io/hextra/docs/advanced/multi-language/
-