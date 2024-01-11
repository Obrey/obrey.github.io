---
created: 2024-01-11 12:22
updated: 2024-01-11 20:29
date: 2024-01-11
tags:
  - Hugo
  - Git
  - Github
  - GithubPages
  - Hextra
aliases:
  - 휴고
  - 깃
  - 깃허브
  - 깃허브페이지
  - 헥스트라
MOC: "[[../../09. MOC/Develop MOC|Develop MOC]]"
title: tags 만들기
weight: "9"
---
---

### 연결문서
- 

### 메모
테마에 tags를 추가하고 싶었고, 결국 성공했습니다.

#### 방법
태그가 있는 다른 테마 중에 마음에 들면서 추가시킬만한 것을 찾습니다. 저는 깔끔하고 잘 어울릴 것 같은 ‘mini’ 테마를 선택했습니다. ‘mini’ 테마의 ‘layout’ 폴더에서 'terms.html’과 ‘tags.html’ 파일을 다운로드했습니다. 그리고 내 테마의 HTML 파일을 참고하여, 특히 navbar와 같은 공통 부분을 유지하면서, 다운로드한 'terms.html’과 'tags.html’의 내용을 대체했습니다.

**이 과정에서 태그를 닫지 않아서 문제가 발생했습니다. 따라서 대체한 부분 아래에 태그를 닫는 것을 잊지 말아야 합니다.**

#### hugo.yaml
메뉴를 추가해야 합니다. 아래 yaml 코드를 참고하세요.

```yaml.hugo
menu:
  main:
    - identifier: documentation
      name: Iolite
      pageRef: /docs
      weight: 1
    - identifier: showcase
      name: Showcase
      pageRef: /showcase
      weight: 2
    - identifier: blog
      name: Blog
      pageRef: /blog
      weight: 3
    - identifier: about
      name: About
      pageRef: /about
      weight: 4
    - name: tags
      pageRef: /tags
      weight: 6
    - name: Search
      weight: 10
      params:
        type: search
    - name: GitHub
      weight: 15
      url: "https://github.com/imfing/hextra"
      params:
        icon: github
```

#### CSS 수정
CSS 수정이 필요합니다. ‘MINI’ 테마의 기존 CSS를 복사하여 붙여넣었는, Hugo로 보는 것은 작동했지만 웹에 게시한 모습은 달랐습니다. 여기서는 Tailwind CSS가 적용되어 있어, 원하는 앵커 태그의 CSS를 복사하여 적용시켰습니다.

최종 화면은 이미지와 같습니다.
![](https://i.imgur.com/6z151dB.png)
![](https://i.imgur.com/MCn5a1q.png)


#### 미운 오리 태그
백조 같은 ‘Hextra’ 테마에 약간 어색한 태그가 추가되었지만, 이 기능이 필요하다고 느껴서 추가했습니다. 디자인적으로는 아쉽지만 기능적으로는 좋아졌습니다.

### 참조
- https://github.com/nodejh/hugo-theme-mini