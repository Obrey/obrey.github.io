---
created: 2024-11-19 14:26
updated: 2024-11-19 14:26
date: 2024-11-19
tags:
  - IndexNow
  - GitHubActions
  - GitHubPages
  - Hugo
aliases: 
links: 
title: GitHub 블로그를 IndexNow로 빠르게 색인하는 방법
weight: 
description: GitHub Pages에서 Hugo로 빌드한 블로그를 IndexNow와 GitHub Actions를 사용해 빠르게 검색 엔진에 색인하는 방법을 알아보세요. API Key 설정부터 배포 기록 삭제까지 안내합니다.
---
## 연결문서
- 

## 메모 
### Hugo 블로그를 GitHub Actions와 IndexNow로 색인하는 방법

Hugo로 정적 웹사이트를 빌드하고 GitHub Pages를 통해 배포하는 경우, 사이트맵을 검색 엔진에 제출하여 인덱싱을 자동화할 수 있습니다. 그러나, 더 빠르게 **검색 엔진**이 내 사이트의 변경 사항을 반영하게 하고 싶다면 **IndexNow** 프로토콜을 사용하는 것이 좋습니다. 이 글에서는 **GitHub Actions**를 사용하여 **Hugo 블로그**와 **IndexNow**를 통합하는 방법을 단계별로 설명하겠습니다. 이를 통해 검색 엔진이 사이트의 변경 사항을 더 빠르게 반영할 수 있으며, **SEO 성과**를 향상시킬 수 있습니다.

### IndexNow
**IndexNow**는 웹사이트 소유자들이 **검색 엔진**에 자신의 사이트 콘텐츠 업데이트를 즉시 알릴 수 있는 프로토콜입니다. 즉, 웹사이트가 새로운 콘텐츠를 만들거나 기존 콘텐츠를 수정하거나 삭제했을 때, 그 변경 사항을 빠르게 검색 엔진에 알려줄 수 있는 시스템입니다.

기존의 검색 엔진은 **크롤러**가 웹사이트를 방문해야만 콘텐츠 변경 사항을 감지할 수 있었습니다. 이 과정은 시간이 오래 걸릴 수 있으며, 중요한 업데이트가 바로 검색 결과에 반영되지 않을 수 있습니다. 반면, **IndexNow**를 사용하면 웹사이트 소유자가 직접 검색 엔진에 알림을 보내어, 검색 엔진이 해당 페이지를 더 빠르게 크롤링하고 인덱싱할 수 있도록 합니다.

#### **IndexNow**를 지원하는 주요 검색 엔진
### 1. **검색 엔진**
IndexNow는 여러 검색 엔진에서 지원하며, 이를 통해 웹사이트의 URL 변경 사항을 빠르게 알릴 수 있습니다.

- **Bing** (Microsoft)
  - IndexNow를 가장 먼저 도입한 검색 엔진 중 하나입니다.
  
- **Yandex**
  - 러시아의 대표적인 검색 엔진으로, Bing과 함께 IndexNow를 지원하고 있습니다.

- **Naver Search Advisor**
  - 한국의 대표적인 검색 엔진으로, IndexNow를 지원하고 있습니다.

- **Google** (검토 중)
  - Google은 아직 공식적으로 IndexNow를 지원하지 않지만, 2022년부터 IndexNow 테스트 및 도입 가능성을 검토 중이라고 발표했습니다.

#### IndexNow의 작동 방식
1. **API 키 생성**: 먼저, 웹사이트 소유자는 IndexNow 프로토콜을 사용하기 위해 고유한 API 키를 생성합니다. 이 API 키는 검색 엔진과의 인증을 위해 사용됩니다.
2. **URL 제출**: 웹사이트에서 콘텐츠가 생성, 업데이트되거나 삭제되면, IndexNow 프로토콜을 통해 검색 엔진에 해당 URL을 제출합니다. 이때 API 키가 포함된 요청을 보냅니다.
3. **검색 엔진 인덱싱**: 검색 엔진은 이 알림을 받고 해당 URL을 크롤링하여, 인덱스에 반영합니다.

저는 Hugo로 Github page를 통해 사이트를 빌드하는데, 문제는 정적인 사이트이기 때문에 indexnow를 사용하기 생각보다 어렵습니다. 그러나, github action을 활용하면 가능합니다.

### Hugo로 GitHub Pages에 블로그 빌드하기

저는 **Hugo**를 사용하여 정적 사이트를 빌드하고, **GitHub Pages**를 통해 배포하고 있습니다. **Hugo**는 빠르고 유연한 **정적 사이트 생성기(static site generator)** 로, Markdown 파일을 기반으로 웹사이트를 생성합니다.

Hugo로 작성된 블로그는 GitHub Pages와 같은 정적 사이트 호스팅 서비스에서 쉽게 배포할 수 있습니다. 이 과정에서 **GitHub Actions**를 활용하면, 코드 푸시(push) 시 자동으로 사이트가 빌드되고 배포되도록 설정할 수 있습니다.

### GitHub Actions

**GitHub Actions**는 GitHub에서 제공하는 **자동화 도구**입니다. 이를 통해 사용자는 **코드 저장소(레포지토리)** 에서 발생하는 다양한 작업을 자동화할 수 있습니다. 주로 **CI/CD(지속적 통합/지속적 배포)** 파이프라인을 설정하는 데 많이 사용되지만, 그 외에도 다양한 작업을 자동화할 수 있습니다.
간단히 말하면, **GitHub Actions**는 특정 조건이 충족되면(예: 코드 푸시, PR 생성 등) 미리 정해둔 작업들을 자동으로 실행해주는 기능입니다.

### 전반적인 방법
#### 방법1
1. API Key 생성하기
2. Github 저장소 설정에서 Sercet Key 생성하기
3. 사이트 루트디렉토리에 API키가 생성되도록 하여 사용자 인증 받기
4. indexing이 되면 확인 하기

#### 방법2
1. API Key 생성하기
2. Github 저장소 설정에서 Sercet Key 생성하기
3. 스태틱 폴더에 APIKEY.txt를 올리고 푸쉬하기
4. 사용자 인증을 받기
5. APIKEY.txt를 지우고, 깃기록과 배포기록, github action기록 모두 지우기

#### 사이트 루트디렉토리에 API키가 생성
먼저 GitHub 저장소의 Settings > Security > Actions로 들어갑니다.

![시크릿 키 발급 경로 설명](https://i.imgur.com/B05CuMc.png)

그 후, New repository secret 버튼을 클릭합니다.

![시크릿 키 생성 버튼 설명](https://i.imgur.com/Vg5HAtg.png)
다음과 같이 Secret 이름은 INDEXNOW_KEY로 하고, 값에는 발급받은 API 키를 입력합니다.

![INDEX NOW KEY SECRET 설정](https://i.imgur.com/tgKZmPS.png)

그리고 Add secret을 누르면 우리가 indexnow에서 발급받은 api키를 안전하게 사용할 수 있습니다.

### Github action 설정

IndexNow는 사이트 소유자임을 확인하는 작업이 필요합니다. 이 작업은 사이트 루트 디렉토리에 API 키 파일이 있는지 확인하는 방식으로 이루어집니다.
다음과 같은 GitHub Action 워크플로우 코드를 추가하여 인증 경로를 생성할 수 있습니다:

#### API Key 인증 경로 생성
```yaml
      # API Key 저장하는 부분 추가됨
      - name: Save API key to static folder
        run: echo "${{ secrets.API_KEY }}" > static/${{ secrets.API_KEY }}.txt
```
이 코드를 통해 Hugo 빌드 전에 API 키 파일이 static 폴더에 저장되도록 설정할 수 있습니다. 이렇게 하면 웹사이트 주소 /apikey.txt에 방문했을 때 API 키가 존재하게 되어 인증이 가능합니다.

전체코드는 이렇습니다.
```yaml
# Sample workflow for building and deploying a Hugo site to GitHub Pages with IndexNow submission
name: Deploy Hugo site to Pages and Submit to IndexNow

on:
  # Runs on pushes targeting the default branch
  push:
    branches:
      - main

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.120.2
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb          

      - name: Install Sass
        run: npm install -g sass

      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive
          fetch-depth: 0

      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v3

      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"

      # API Key 저장하는 부분 추가됨
      - name: Save API key to static folder
        run: echo "${{ secrets.INDEXNOW_KEY }}" > static/${{ secrets.INDEXNOW_KEY }}.txt

      - name: Build with Hugo
        env:
          # For maximum backward compatibility with Hugo modules
          HUGO_ENVIRONMENT: production
          HUGO_ENV: production
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v2
        with:
          path: ./public

  # Deployment job to GitHub Pages
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2

  # IndexNow submission job after deployment is complete
  check-and-submit:
    runs-on: ubuntu-latest
    needs: deploy # This ensures that the IndexNow submission happens after deployment is complete.
    steps:
      - name: Submit sitemap to IndexNow using indexnow-action
        uses: bojieyang/indexnow-action@v2
        with:
          sitemap-location: 'https://obrey.github.io/sitemap.xml'
          key: ${{ secrets.INDEXNOW_KEY }}
```
이런식으로 빌드와 함께 인증이 되도록 실행했습니다.

#### 직접 static에 api key를 올리기
api key가 유출되는 것에 그렇게 민감하지 않거나 자신의 git 기록과 배포 기록을 지워도 상관이 없다면, github action에서 인증경로를 생성하지 않고, 바로 인증을 완료할 수 있습니다.
루트디렉토리의 static폴더에 인증받은 api key.txt 파일을 넣고 배포합니다. 자신의 주소/apikey.txt를 입력했을때 제대로 나온다면 이제 인증받을 준비가 되었습니다.

#### python을 통해 간단히 인증 받기
GitHub Action으로 인증하려 했으나 문제가 발생하여 Python 코드를 사용해 직접 인증 과정을 처리했습니다:
```python
import requests


def submit_to_indexnow(api_key, host, urls):
    if isinstance(urls, str):
        urls = [urls]  # 단일 URL을 리스트로 변환

    payload = {
        "host": host,
        "key": api_key,
        "keyLocation": f"https://{host}/{api_key}.txt",
        "urlList": urls
    }

    try:
        response = requests.post(
            "https://api.indexnow.org/indexnow",
            json=payload,
            headers={'Content-Type': 'application/json'}
        )

        if response.status_code in [200, 202]: 
            print(f"성공: {len(urls)}개의 URL이 제출되었습니다.")
            print(f"상태 코드: {response.status_code}")
            if response.status_code == 202:
                print("(202 Accepted: 요청이 접수되었습니다.)")
            return True
        else:
            print(f"실패: HTTP {response.status_code}")
            print(f"응답: {response.text}")
            return False

    except Exception as e:
        print(f"오류 발생: {str(e)}")
        return False


# 사용 예시
if __name__ == "__main__":
    # 설정
    API_KEY = YOUR_INDEXNOW_KEY  # 여기에 기존 API 키를 입력하세요
    HOST = "obrey.github.io"  # 여기에 도메인을 입력하세요

    # 제출할 URLs
    urls_to_submit = [f"https://{HOST}/"]

    # URL 제출
    submit_to_indexnow(API_KEY, HOST, urls_to_submit)
```
성공적으로 200 응답 코드를 받으면 인증이 완료된 것입니다.

#### github action으로 시간마다 인덱싱하기
github action을 통해 배포하는게 아닌, 매일 정해진 시간에 인덱싱 하도록 코드를 생성할 수 있습니다. 

```yaml
name: "IndexNow"
on:
  schedule:
    - cron: '0 2 * * *'

jobs:
  submit-sitemaps:
    runs-on: ubuntu-latest
    steps:
      - name: IndexNow
        uses: bojieyang/indexnow-action@v2
        with:
          sitemap-location: 'https://obrey.github.io/sitemap.xml'
          key: ${{ secrets.INDEXNOW_KEY }}
```
이 workflow를 사용하면 정해진 시간에 직접 사이트맵 색인을 실시합니다.

#### git log 지우고 배포기록 모두 삭제하기
API 키 유출 방지를 위해 static 폴더에 업로드한 APIKEY.txt 파일과 관련 기록들을 모두 삭제할 수 있습니다.

##### git 기록 지우기
 Git 내역을 모두 삭제하고 새롭게 시작하려면, 기존의 커밋 히스토리를 제거하고 새로운 커밋을 생성하는 방법을 사용할 수 있습니다. 이 작업은 주의가 필요하며, 특히 원격 저장소에 강제로 푸시해야 하므로 **데이터 손실**에 유의해야 합니다. 다음은 Git 내역을 완전히 삭제하는 방법입니다.

```bash
git checkout --orphan latest_branch
git add -A
git commit -m "Initial commit"
git branch -D main
git branch -m main
git push -f origin main
```
이 과정을 통해 기존 커밋 히스토리를 제거하고 새로운 커밋 하나만 남길 수 있습니다.

##### 배포 기록 지우기
배포 및 워크플로우 실행 기록도 함께 삭제하려면 다음 워크플로우 파일을 사용할 수 있습니다.

```yaml
name: Delete Deployments and Workflow Runs

on:
  push:
    branches:
      - main

jobs:
  cleanup:
    runs-on: ubuntu-latest
    permissions:
      deployments: write
      contents: write
      statuses: write
    steps:
      - name: 🗑 Delete deployment
        uses: strumwolf/delete-deployment-environment@v2
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          environment: github-pages
          onlyRemoveDeployments: true

  del_runs:
    runs-on: ubuntu-latest
    permissions:
      actions: write
      contents: read
    steps:
      - name: Delete workflow runs
        uses: Mattraks/delete-workflow-runs@v2
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          repository: ${{ github.repository }}
          retain_days: 0               # 모든 워크플로우 실행 기록 삭제
          keep_minimum_runs: 0         # 최소 실행 기록 유지하지 않음
```

이 워크플로우는 배포 기록과 워크플로우 실행 기록을 모두 제거하여 민감한 정보가 남지 않도록 합니다.

### 결론

이번 글에서는 **IndexNow**와 **GitHub Actions**를 활용해 빠르게 인덱싱하는 방법과 배포 기록 및 Git 히스토리를 안전하게 관리하는 방법을 다루었습니다. 특히 정적 사이트와 같이 일반적인 크롤링 방식으로는 느리게 반영될 수 있는 경우에는 매우 유용한 방법입니다.보안 문제에도 주의를 기울여야 하며, 특히 API 키와 같은 민감한 정보를 다룰 때는 철저한 관리가 필요합니다.

## 참조
- https://github.com/bojieyang/indexnow-action