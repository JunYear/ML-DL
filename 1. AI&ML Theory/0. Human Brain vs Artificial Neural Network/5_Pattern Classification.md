# 패턴의 유형
- 패턴이란 어떤 객체를 정량적으로 표현한 것을 의미함.
- 공간 패턴과 시변 패턴으로 구분됨.
	- 공간패턴: 공간적 분포에 의해서만 특성이 결정되고 시간에 따라 특성이 변하지 않는 패턴을 의미함. 문자, 영상 등이 속함
	- 시변 패턴: 시간에 따라 특성이 변하는 패턴을 의미함. 음성 신호, 온도 변화, EKG 파형 등이 속함.

# 패턴 분류 시스템
## 트랜스듀서
- 분류하고자 하는 실제의 데이터를 획득하여 신경망이 처리하기 용이한 형태로 변환하는 기능을 수행함.
- 여기서 용이한 형태는 신경망의 구조에 따라 **디지털 혹은 아날로그 데이터**를 뜻함.
- 트랜스 듀서의 출력을 **패턴 벡터**라고 함.

패턴 벡터: $[x_1 x_2 ... x_n]$ , 화소수: $p$
## 특징 추출기
- 패턴 벡터를 입력받아 패턴 분류에 영향을 미치는 중요한 특징만을 선택하여 **특징 벡터**를 출력함.
- 해상도가 높은 경우엔 패턴 벡터의 데이터 양이 너무 많기에 패턴 분류 소요 계산 시간의 증가와 분류할 패턴들 간의 특징이 잘 표현되지 않아 오히려 성능이 떨어짐.
- 이러한 단점 보완을 위해 특징 추출기를 사용함.

특징 벡터 $X = [x_1 x_2 ... x_n]$ , ( $n < p$ ) , 입력층의 뉴런의 수: $n$
출력 클러스터 $Y = [y_1 y_2 ... y_m]$ , 출력층의 뉴런의 수: $m$
## 분류기
- 특징 벡터를 입력받아 그 특징에 따라 특정 클러스터로 분류하는 기능을 수행함.
- 패턴을 분류하는 경우에는 신경망에 어떤 패턴을 입력하여 최대 출력이 나오는 뉴런을 선택함으로써 입력된 패턴이 특정 클러스터에 속한다고 판단함.

# 판별 함수
## 판단 경계선
- 일반적으로 유사한 특징을 갖는 패턴들은 인접한 영역에 분포되어 하나의 클러스터를 형성하고, 상이한 특징을 갖는 패턴들은 다른 영역에 또 다른 클러스터를 형성함.
- 따라서, 특정한 **분리면(판단면)** 을 이용하여 클러스터들을 분리 시킨다면 패턴 분류가 가능해짐.
- 2차원 패턴 공간에서의 판단면 (판단 경계선)
	- $w_1x_1 + w_2x_2 + b = 0$
- 판단 경계선을 벡터 형태로 표현
	- $XW = 0$
	- $$X = [x_1 x_2 1], W = \begin{bmatrix}w_1\\ w_2 \\ b \end{bmatrix}$$

## 판단면을 정의하는 판별 함수
- 판단면을 정의하는 함수 $d(X)$를 판별 함수라고 함
- $d_1(X)$ 와 $d_2(X)$ 는 각각 클러스터 1과 클러스터 2에 속해 있는 패턴 $X$ 에 대한 판별 함수의 값임.
- 2개의 클러스터로 분류하는 경우는 다음과 같음.
	- $d_1(X) < d_2(X) \Rightarrow$ 패턴 $X$는 클러스터 1에 속함.
	- $d_1(X) > d_2(X) \Rightarrow$ 패턴 $X$는 클러스터 2에 속함.
	- $d_1(X) = d_2(X) \Rightarrow$ 패턴 $X$가 어떤 클러스터에 속하는 지 알 수 없음.
- 패턴 공간이 n차원인 경우에는 판단면이 다음과 같이 n차 하이퍼 평면이 됨.
	- $w_1x_1 + w_2x_2 + ... + w_nx_n + b = 0$