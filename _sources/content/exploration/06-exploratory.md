# cellxgene을 이용한 탐색적 분석

## cellxgene 소개

Cellxgene(셀-바이-진으로 발음)은 단일 세포 전사체 데이터셋을 위한 대화형 데이터 탐색기입니다. 작동 예는 [여기](https://www.kidneycellatlas.org/fetal-kidney-immune)에서 볼 수 있습니다.

입력으로 사전 계산된 저차원 임베딩(예: tSNE 또는 UMAP)과 선택적으로 추가 메타데이터(예: 주석이 달린 조직 유형 또는 사전 계산된 클러스터 레이블)를 포함하는 `h5ad` 파일(AnnData)을 사용합니다.

지금까지 작업해 온 뇌 데이터를 cellxgene에 로드한 다음, 데이터셋을 좀 더 자세히 탐색하는 시간을 갖겠습니다.

## cellxgene 시작하기

0. 아직 설치하지 않았다면, [이 페이지](https://chanzuckerberg.github.io/scRNA-python-workshop/intro/setup.html) 하단의 지침에 따라 cellxgene을 설치하고 설치를 확인하십시오.
1. 터미널 창을 엽니다(Mac: `응용 프로그램 > 유틸리티 > 콘솔`, Windows: `시작 > 모든 프로그램 > 보조프로그램 > 명령 프롬프트`).
1. 터미널에서 `cellxgene launch path/to/course/folder/content/data/brain_clusters.h5ad --open`을 입력합니다.
   `path/to/course/folder`를 컴퓨터에 있는 강의 폴더의 올바른 파일 경로로 바꿔야 합니다.
   예를 들어, 데스크톱에 강의 폴더가 있는 mac 사용자의 경우 `Desktop/scRNA-python-workshop/content/data/brain_clusters.h5ad`를 입력합니다.

## 연습: 데이터 탐색

Cellxgene은 다양한 탐색 작업에 사용할 수 있습니다. 시작하는 데 도움이 되는 몇 가지 예는 다음과 같습니다.

### 교란 요인 찾기

`mouse.id`로 색칠해 보십시오. 임베딩된 데이터의 구조가 세포가 어떤 마우스에서 왔는지에 따라 결정되는 것처럼 보입니까, 아니면 서로 섞여 있습니까? 그것은 무엇을 말해줍니까?
메타데이터의 다른 가능한 교란 요인 각각에 대해 이 작업을 시도해 보십시오. 무엇을 관찰하셨습니까?

### QC 클러스터 할당

`mouse.sex`로 색칠하고 `louvain`(클러스터 레이블)을 확장합니다. 우리가 식별한 클러스터는 한 마우스의 모든 세포로 구성되어 있습니까, 아니면 서로 섞여 있습니까? 그것은 무엇을 말해줍니까?

### 유전자 발현 시각화

가장 좋아하는 유전자를 추가하고 발현으로 색칠합니다. 대부분의 유전자는 대부분의 세포에서 발현되지 않으므로 분포를 보려면 `클립` 기능(오른쪽 상단 메뉴)을 사용해야 할 수 있습니다.
이제 세포 유형(`cell_ontology_class` 메타데이터 확장)에 걸친 분포를 살펴보십시오. 흥미로운 차이점이 있습니까?

### 세포 그룹 비교

흥미로운 세포 그룹을 선택하여 `Set1`에 할당합니다. 다른 세포 그룹에 대해 반복하고 `Set2`에 저장합니다. `차등 발현 계산`을 클릭합니다. 반환된 차등 발현 유전자에 대해 어떻게 생각하십니까? p-값이 의미가 있습니까? 이러한 p-값을 해석하는 데 있어 주의할 점은 무엇입니까? 로그-폴드 변화는 어떻습니까?

### 세포 유형 할당

마커 유전자를 기반으로 세포 집단을 식별하는 연습을 하고, `새 레이블`을 만들어 관찰 결과를 저장합니다.

## 자료

cellxgene에 대한 자세한 내용은 [여기에서 설명서를 읽으십시오](https://chanzuckerberg.github.io/cellxgene/).

기능을 요청하거나 버그를 보고하려면 [github 리포지토리를 확인하십시오](https://github.com/chanzuckerberg/cellxgene/issues).

다른 사용자와 채팅하거나 질문, 의견 또는 제안 사항이 있는 개발자에게 연락하려면 [`#cellxgene-users` 슬랙 채널에 참여하십시오](https://join-cellxgene-users.herokuapp.com/).