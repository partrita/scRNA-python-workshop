# 단일 세포 RNA-seq 데이터 분석 (Python)

# [여기에서 강의 내용을 확인하세요](https://chanzuckerberg.github.io/scRNA-python-workshop/)

## 강의 목표

오늘날에는 고처리량 시퀀싱(scRNA-seq)을 사용하여 단일 세포에서 게놈 전체의 전사체 데이터를 얻을 수 있습니다. 이 하루 워크숍의 목표는 모든 배경(전산 또는 기타)의 과학자들이 자신의 scRNA-seq 데이터를 탐색하는 데 자신감을 갖도록 돕는 것입니다. 구체적으로, 우리는 학생들이 다음을 할 수 있는 능력을 갖추고 떠나기를 바랍니다:

- scRNA-seq 데이터를 다루는 일반적인 워크플로우 이해
- scRNA-seq 분석에서 가장 일반적인 함정 일부를 예측하고 피하기
- 분석적 선택에 내재된 절충안에 대한 직관 구축
- 단일 세포 분석을 위한 최신 Python 기반 도구를 편안하고 자신있게 사용
- 공동 작업자와 더 나은 대화 나누기
- 추가 정보 및 지원을 찾을 수 있는 곳 알기

### 다루는 주제

다음의 기본 사항을 다룰 것입니다:

- 품질 관리
- 정규화
- 차원 축소
- 클러스터링
- 차등 발현
- 탐색적 분석

## 강의의 비목표

우리는 이 워크숍 전반에 걸쳐 현재의 모범 사례를 통합하고 방법론적 선택에 대한 직관을 구축하려고 노력했습니다. 그러나 단일 세포 데이터는 복잡하고 이 분야는 빠르게 발전하고 있습니다. 또한 이 분석의 많은 측면에서 이 분야는 아직 모범 사례에 대한 합의에 도달하지 못했습니다. 하루 과정으로는 모든 관련 고려 사항과 도구를 다룰 수 없습니다. 여기서는 기초적인 직관을 구축하고 합리적인 런타임으로 Python에서 사용할 수 있는 주제와 도구를 우선적으로 다루었습니다. 하루라는 시간표를 감안할 때, 우리는 발현 행렬에서 시작하고 원시 데이터 처리는 다루지 않기로 결정했습니다. 포괄적인 가이드는 아니지만, 이것이 단일 세포 분석에 접근하는 디딤돌이 되기를 바랍니다.

## 전제 조건 및 자료

워크숍은 설명적인 토론과 실습이 번갈아 가며 진행됩니다. **완전히 참여하려면 모든 필수 패키지가 설치된 노트북을 가져오시는 것을 강력히 권장합니다.** [여기](https://chanzuckerberg.github.io/scRNA-python-workshop/intro/setup.html)의 지침을 따르십시오.

이 과정은 Python에 대한 기본적인 지식이 있는 분들을 대상으로 합니다(예: 소프트웨어 카펜트리 워크숍에서 다루는 수준). Jupyter 노트북과 명령줄에 대한 기본적인 지식이 있으면 도움이 되지만 필수는 아닙니다.

다음 입문 자료를 권장합니다:

- **Python**: ["Python에서의 플로팅 및 프로그래밍"](http://swcarpentry.github.io/python-novice-gapminder/)에 대한 소프트웨어 카펜트리 워크숍
- **Python**: [Codecademy Python3 과정](https.www.codecademy.com/learn/learn-python-3) (체험판으로 무료).
- **명령줄**: [Codecademy 명령줄 과정](https://www.codecademy.com/learn/learn-the-command-line) (체험판으로 무료).
- **Jupyter 노트북**: [Coderefinery Jupyter 워크숍](https://coderefinery.github.io/jupyter/).

## 추천 자료

## [단일 세포 RNA seq 데이터 분석](https://scrnaseq-course.cog.sanger.ac.uk/website/index.html)

많은 강의 내용의 원본 출처; 2일 과정으로서, 분석 방법에 대한 더 넓은 개요와 원시 데이터에서 발현 행렬을 생성하는 가이드를 포함합니다. 예제는 R로 구현되었지만 개념적 토대는 광범위하게 적용 가능합니다.

## [단일 세포 RNA-seq 분석의 현재 모범 사례: 튜토리얼](https://www.embopress.org/doi/full/10.15252/msb.20188746)

많은 방법론적 절충안과 모범 사례에 대한 현재의 이해에 대한 명확한 설명. 주로 Python으로 구현된 심층 튜토리얼을 포함합니다.

## 개발, 재사용 및 기여

### 내용

이 과정은 [원래 Hemberg Lab에서 개발](https://scrnaseq-course.cog.sanger.ac.uk/website/index.html)했으며, [Sidney Bell](https://twitter.com/sidneymbell)과 Chan Zuckerberg Initiative의 전산 생물학 팀이 (허가를 받아) Python에 맞게 축약하고 수정했습니다.
우리는 원본 강의 자료의 저자인 Vladimir Kiselev, Tallulah Andrews, Jennifer Westoby, Davis McCarthy, Maren Büttner, Jimmy Lee, Krzysztof Polanski, Sebastian Y. Müller, Elo Madissoon, Stephane Ballereau, Maria Do Nascimento Lopes Primo, Rocio Martinez Nunez, Martin Hemberg의 노고에 깊이 감사합니다.

또한 [Luecken and Theis, 2019](https://www.embopress.org/doi/full/10.15252/msb.20188746)에서 제시한 관행과 구성을 통합했으며, 그들의 노고에 감사드립니다.

이 커리큘럼은 2019년 10월 18일 일리노이주 시카고에서 열린 CZI 후원 워크숍의 하루 동안 처음으로 강의되었습니다.

### 기여

우리는 과학계 구성원들이 [github](https://github.com/chanzuckerberg/scRNA-python-workshop)를 통해 업데이트와 개선 사항을 제출하는 것을 따뜻하게 환영하고 권장합니다.

우리는 원본 자료의 라이선스를 준수합니다:

> 모든 강의 자료는 GPL-3에 따라 라이선스가 부여됩니다. 누구나 scRNA-seq 데이터 분석에 대해 배우기 위해 자료를 살펴볼 수 있습니다. 자신의 교육에 자료를 사용할 계획이라면, 원본 자료에 대한 적절한 인용을 제공하는 것 외에 Hemberg 연구실에 알려주시면 감사하겠습니다.

### 연락처

원본 자료의 개념적 질문에 대해서는 [Vladimir Kisilev](vladimir.yu.kiselev@gmail.com)에게 문의하십시오.
Python 적용에 대한 질문은 [Sidney Bell](twitter.com/sidneymbell)에게 문의하십시오.