---
title: Amethyst fork하기
weight: "4"
prev: 
next:
---
---

### 연결문서
- 

### 메모
#### 기본 테마 fork 하기
#### 기본 테마 포크하기

> [!NOTE] 포크는 저장소의 복사본을 의미합니다. 저장소를 포크하면 원본 프로젝트에 영향을 주지 않고 변경 사항을 자유롭게 실험할 수 있습니다.

![](https://i.imgur.com/fQUojNv.png)

Amethyst 프로젝트의 GitHub 저장소에 이동합니다. 그런다음 리포지토리를 자신의 Github 계정으로 포크합니다. 

![](https://i.imgur.com/c7mRrBw.png)

꼭, 공개 설정으로 리포지토리를 생성해야 합니다. 포크를 하면 동일한 이름의 리포지토리가 생성 되었습니다.

#### 로컬과 연동하기
저장소를 포크한 후에는 파일을 컴퓨터에 로컬로 다운로드해야 합니다. 깃허브 파일을 다운로드 할 폴더에서 빈 공간에 마우스 오른쪽 버튼을 클릭하여 '터미널에서 열기’를 실행합니다. 그리고 다음의 명령을 입력합니다.

```terminal
git clone https://github.com/YOUR-USERNAME/amethyst
```
로컬에서 파일이 다운로드 된 것을 확인하면 이제 포크가 완료된 것입니다.

#### Github 페이지에서 호스팅
![](https://i.imgur.com/4ASSWwX.png)

포크된 자신의 저장소의 `Setting`으로 이동합니다.

![](https://i.imgur.com/9AnuGCw.png)

왼쪽 탭에서 `Pages`를 선택합니다.

![](https://i.imgur.com/RGdRPog.png)
`Branch`에서 자신의 파일이 있는 브랜치를 선택합니다. 이 테마는 `main` 브랜치이므로 `main`을 선택한 후 `Save`버튼을 누릅니다.

그럼 이제 `https:://USER-NAME.github.io/REPO-NAME`으로 파일이 보이는 것을 확인할 수 있습니다.

### 참조
- 