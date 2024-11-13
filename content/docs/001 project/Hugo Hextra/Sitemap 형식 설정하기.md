---
created: 2024-11-13 20:34
updated: 2024-11-13 20:34
date: 2024-11-13
tags:
  - Hugo
  - Sitemap
  - GithubPages
  - Github
aliases: 
links: 
title: Sitemap 형식 설정하기
weight: 
description: 웹사이트의 검색 엔진 최적화를 위한 요소, 사이트맵. Hugo에서 커스텀 사이트맵(sitemap.xml)을 설정하고 SEO를 향상시키는 방법을 알아보세요.
---
## 연결문서
- 

## 메모 
### 사이트맵
사이트맵(sitemap.xml)은 웹사이트의 모든 페이지와 콘텐츠 목록을 포함한 파일로, 검색 엔진이 웹사이트를 더 효율적으로 탐색하고 인덱싱할 수 있도록 돕습니다. 이 파일은 보통 XML 형식으로 작성되며, 각 페이지의 URL, 업데이트 날짜, 페이지 중요도, 그리고 웹사이트 내 다른 페이지와의 관계 등을 포함할 수 있습니다. 

#### 주요 역할
1. **검색 엔진 크롤링 지원**: 사이트맵은 구글과 같은 검색 엔진이 웹사이트 구조를 쉽게 이해하여 중요한 페이지가 누락되지 않고 검색 결과에 잘 반영되도록 돕습니다.
2. **페이지 우선순위 전달**: 각 페이지에 대한 중요도를 지정할 수 있어, 검색 엔진에 우선적으로 인덱싱할 페이지를 알려줄 수 있습니다.
3. **새 페이지 및 업데이트 정보 제공**: 사이트에 새로운 콘텐츠가 추가되거나 페이지가 업데이트된 경우, 사이트맵을 통해 이를 검색 엔진에 빠르게 알릴 수 있습니다.

#### 구성 예시
```xml
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://www.example.com/</loc>
    <lastmod>2023-01-01</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://www.example.com/about</loc>
    <lastmod>2023-01-01</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
</urlset>
```

### Hugo와 사이트맵
Hugo에서는 사이트맵 파일(sitemap.xml)이 기본적으로 자동 생성되지만, 생성된 형식이 단순한 텍스트로 표시되어 가독성이 부족할 수 있습니다. 빙과 구글 서치 콘솔에서는 이 사이트맵을 잘 인식하지만, 가시성을 개선하기 위해 직접 형식을 조정할 수 있습니다.

#### Custom sitemap.xml 생성하기
```
layouts
└── _default
    └── sitemap.xml
```
`layouts/_default/sitemap.xml` 경로에 아래 코드를 포함하여 파일을 생성합니다.

```sitemap.xml
{{ printf "<?xml version=\"1.0\" encoding=\"utf-8\" standalone=\"yes\"?>" | safeHTML }}
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {{- range .Pages -}}
  <url>
    <loc>{{ .Permalink }}</loc>
    {{- if not .Lastmod.IsZero }}
    <lastmod>{{ .Lastmod.Format "2006-01-02T15:04:05-07:00" }}</lastmod>
    {{- end }}
  </url>
  {{- end -}}
</urlset>
```

#### hugo.yaml 설정 수정하기
Hugo 설정 파일(hugo.yaml)에서 사이트맵 관련 설정을 아래와 같이 추가합니다.

```yaml
sitemap:
  changefreq: daily
  priority: 0.5
  filename: sitemap.xml
```

이렇게 설정을 마치면 사이트맵이 구조화된 XML 형식으로 나타나 가독성이 높아집니다.

### 결론
이렇게 사이트맵을 설정하면 검색 엔진이 웹사이트의 콘텐츠를 빠르고 정확하게 인식할 수 있어 SEO에 긍정적인 영향을 줄 수 있습니다. 특히 Hugo를 사용하는 경우, 위 설정을 통해 기본 사이트맵보다 더욱 가독성 높은 파일을 제공할 수 있습니다. 사이트맵은 한 번 설정해 두면 큰 수정 없이 계속 활용할 수 있으므로, 꼭 챙겨두는 것이 좋습니다.

## 참조
- 