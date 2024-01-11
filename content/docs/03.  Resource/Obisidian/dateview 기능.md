---
created: 2024-01-10 14:02
updated: 2024-01-11 20:34
date: 2024-01-10
tags:
  - Obsidian
  - Dataview
  - Plugin
aliases:
  - 옵시디언
  - 데이터뷰
  - 플러그인
MOC: "[[../../09. MOC/Obsidian MOC|Obsidian MOC]]"
title: dateview 기능
weight: 
---
---

### 연결문서
- [Hugo Amethyst index](../../../01.-project/hugo-amethyst)
- [Hugo Hextra index](../../../01.-project/hugo-hextra)
- [Hugo PaperMod index](../../../01.-project/hugo-papermod)

### 메모
#### dataview
다양한 파일과 휴고 사용에 따라 dataview 사용을 해야한다는 결론을 내렸습니다. 이유는 index할 때 너무 불편했습니다. hugo에선 weight로 넘버링을 하기 때문에 파일에 숫자가 들어가지 않는 걸 결론내렸는데, 없으니까 파일의 순서를 정리하기 힘들었습니다. dataview는 간단하게 메타데이터를 이용하여 원하는 파일들을 표 형식으로 볼 수 있습니다. 
먼저 코드블럭을 열어 `dataview`를 작성한 후 여러 조건에 맞게 작성하면 됩니다.

#### gpt활용
이 옵시디언에서 작성하면 당연히 코드가 나올 것 같아서 링크를 올렸는데, 이에 맞게 작성하면 되고, 빙이나 gpt에게 옵시디언의 dataview 플러그인을 아냐고 물어본 후, 코드를 작성하면 생각보다 맞는 문법으로 정리해줍니다.

##### 특정 폴더에 해당하는 데이터뷰
```
TABLE title, date, weight
FROM "myFolder"
SORT weight asc
LIMIT 10
```
이렇게 수정해주었습니다. 

##### `index`텍스트를 가진 파일
index 텍스트를 가진 마크다운 파일을 보고싶다고 하니,
```
TABLE title, date, weight
FROM "Hugo PaperMod"
WHERE contains(title, "index")
SORT weight asc
LIMIT 10
```
이런식으로 짜주더군요.

##### 파일 예외
몇가지 파일이 index에 걸려서 나와, 예외처리를 하고싶다고 하니,
```
TABLE title, date, weight
FROM "01. Project"
WHERE contains(title, "index") AND file.name != "myFile"
SORT weight asc
LIMIT 10
```
짜주었습니다. 데이터뷰도 gpt를 활용하여 사용하면 좀 더 빠르게 데이터뷰를 배우고 구조화 시킬 수 있습니다.

### 참조
- https://blacksmithgu.github.io/obsidian-dataview/reference/sources/