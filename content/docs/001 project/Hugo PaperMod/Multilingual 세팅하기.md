---
created: 2024-01-08 18:25
updated: 2024-01-10 13:16
date: 2024-01-08
tags:
  - Git
  - Github
  - GithubPages
  - PaperMod
  - Multilingual
aliases:
  - 깃
  - 깃허브
  - 깃허브페이지
  - 페이퍼모드
  - 다국어
MOC: "[[../../09. MOC/Develop MOC]]"
title: Multilingual 세팅하기
weight: "6"
---
---

### 연결문서
- [Multilingual 세팅 구상](../multilingual-세팅-구상)

### 메모
#### `i18n` 폴더 생성
기본 폴더에 `i18n` 폴더를 생성하고, 해당 폴더에 작동하려는 서브 언어에 해당하는 `lang.yaml` 파일을 추가합니다. 저는 개발자의 깃허브 저장소에서 해당 파일을 가져왔습니다.

#### `hugo.yaml` 설정
다음 설정을 `hugo.yaml` 파일에 추가합니다.

```hugo.yaml
defaultContentLanguage: kr
defaultContentLanguageInSubdir: false
languages:
  kr:
    weight: 1
    languageName: 한국어
    languageCode: kr
    contentDir: content/kr/
    title: 제목
    menu:
      main:
        - name: 게시글
          url: /posts/
          weight: 4
        - name: 아카이브
          url: /archives/
          weight: 5
        - name: 검색
          url: /search/
          weight: 10
        - name: 태그
          url: /tags/
          weight: 10
        - name: 소개
          url: /about/
          weight: 15
  en:
    weight: 2
    languageName: English
    languageCode: en
    contentDir: content/en/
    title: title
    menu:
      main:
        - name: Posts
          url: /posts/
          weight: 4
        - name: Archive
          url: /archives/
          weight: 5
        - name: Search
          url: /search/
          weight: 10
        - name: Tags
          url: /tags/
          weight: 10
        - name: About
          url: en/about/
          weight: 15
```

- `defaultContentLanguage: kr`로 설정하여 기본 언어를 한국어로 설정합니다.
- `defaultContentLanguageInSubdir: false`로 설정하여 기본 언어에도 주소 뒤에 `/lang/`을 붙입니다. 예: 주소/kr/ 
- `contentDir: content/lang`: 위 경로의 폴더에 언어 폴더를 생성합니다. 이 설정을 하지 않아도 됩니다. 저는 따로 설정이 편리하여 이 방법으로 했지만 contentDir 세팅을 하지 않고 같은 디렉토리 내에 개별로 name.en.md 형식으로 설정하는 방법도 있습니다.

#### `content` 파일 설정
위의 코드처럼 각 언어별로 메뉴 이름을 선택할 수 있습니다.contentDir 설정 시 주의할 점은, 서브 언어의 경우 각각 파일의 경로를 다르게 설정해야 할 수도 있습니다. 예를 들어, `en` 폴더의 `archive`의 경로는 다음과 같이 설정해야 합니다.

```archive.md
title: "Archive"
layout: "archives"
url: "/en/archives/"
summary: archives
```
이렇게 url를 지정해야 합니다.

결론적으로, 멀티링구얼 구현에 성공했습니다. 이제 열심히 글을 작성하면 됩니다.

### 참조
- 