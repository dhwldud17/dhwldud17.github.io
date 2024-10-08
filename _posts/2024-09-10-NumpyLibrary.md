
---
title: [이론1] Numpy 라이브러리
categories: [AI-study, ML]
tags: [이론]     # TAG names should always be lowercase
---


# [이론1] Numpy 라이브러리

---

## 학습 목표
- 머신러닝에서 사용되는 수학적 계산을 위한 numpy 라이브러리의 주요 함수 사용법을 학습합니다.

---

## 목차

### [이론1] Numpy 라이브러리
0. 라이브러리 import 하기
1. Numpy 배열 선언하기
2. 배열 정보 확인하기
3. 배열 자르고 붙이기
4. 배열 연산

---

## [이론1] Numpy 라이브러리

방대한 양의 데이터를 처리하고, 머신러닝에 사용되는 수식을 계산하기 위해서는 **배열**(**array**)을 사용해야 합니다.

예를 들어 $X=\begin{pmatrix}
x_{1,1} & x_{1,2} & ... & x_{1,p} \\ 
x_{2,1} & x_{2,2} & ... & x_{2,p} \\ 
\vdots & \vdots  & \cdots  & \vdots \\ 
x_{N,1} & x_{N,2} & ... & x_{N,p}
\end{pmatrix}$ 라는 행렬로 정리된 데이터가 있다고 하면, 이것을 python 코드로 표현해야 합니다.

이 경우, 행렬 데이터에 대한 계산을 python에서 가장 잘 수행해 줄 수 있는 라이브러리인 **numpy**를 활용할 수 있습니다.

numpy에서는 기본적으로 배열을 행렬로 생각하고, 그 행렬 계산을 쉽게 하도록 도와줍니다.

이번 장에서는 머신러닝을 사용할 때 필요한 numpy의 기본적인 사용법에 대해서 알아봅시다.

#### python 배열

먼저, numpy 배열을 사용하는 이유에 관해서 설명하기 위해, python만을 이용해 배열 계산을 해보겠습니다. 

예를 들어 두 배열 a = [1,2,3,4,5], b = [1,1,1,1,1]의 합을 구하고 싶다면, 가볍게 덧셈 기호를 통해서 구할 수 있을 것처럼 보입니다.

그러나 python에서 배열 덧셈은 아래와 같은 결과를 보여줍니다. 아래의 셀을 실행해보세요.


```python
a = [1, 2, 3, 4, 5]  # 1차원 벡터
b = [1, 1, 1, 1, 1]

a+b
```




    [1, 2, 3, 4, 5, 1, 1, 1, 1, 1]



위 예시처럼 python의 배열은 수학적인 벡터 또는 행렬과는 다른 자료형이기에 수학적 계산에 활용하기 적합하지 않습니다.

 

### 0. 라이브러리 import 하기

import 할 때는 주로 `np` 라는 명칭으로 사용할 수 있도록 합니다.


```python
import numpy as np
```

numpy를 사용하기 위한 준비는 끝났습니다. 

그럼 지금부터 직접 numpy 라이브러리 함수를 직접 사용한 예제를 살펴보도록 하겠습니다. 

 

### 1. Numpy 배열 선언하기

####  numpy 자료형 선언

python 배열과는 numpy 내부에는 벡터와 행렬을 다루기 위한 여러 가지 유용한 메소드들을 제공합니다. 

그중에서도 `array()`는 파이썬의 리스트를 numpy의 배열 자료형으로 변환하는 함수입니다. 

아래 코드를 실행하며 먼저 numpy 기본 자료형을 선언해보겠습니다.


```python
a = np.array([0, 1, 2, 3]) # numPy 배열 초기화
a
```




    array([0, 1, 2, 3])



위 예시처럼 `array()`를 사용하면 numpy 배열 자료형으로 변수를 저장할 수 있습니다.


 

#### arange 함수

numpy에서는 `array()` 외에도 특정한 배열을 만드는 함수들이 존재합니다.

`arange(start,stop,step)` 함수는 **start**부터 **stop**전까지 **step**만큼의 크기로 증가하는 배열을 선언합니다. 


```python
b = np.arange(1,8,2) # 범위(1~8), 2씩 증가
b
```




    array([1, 3, 5, 7])



인자가 1개인 경우 **start = 0, step = 1**로 default 설정됩니다.


```python
# 범위 (0~10) 
b = np.arange(10) 
b
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])



인자가 2개인 경우 **step = 1**으로 default 설정됩니다.


```python
b = np.arange(1,4) # 범위(1~4)
b
```




    array([1, 2, 3])



 

#### zeros, ones, random 함수

이외에도 `zeros`, `ones`, `random` 등으로 특수한 배열을 선언할 수 있습니다.

`zeros()`는 선언하고 싶은 배열의 크기를 입력하여 0으로 채워진 배열을 선언합니다.


```python
np.zeros((3,2)) # (3,2) 크기 0 행렬
```




    array([[0., 0.],
           [0., 0.],
           [0., 0.]])



`ones`는 선언하고 싶은 배열의 크기를 입력하여 1로 채워진 배열을 선언합니다.


```python
np.ones((3,4)) # (3,4) 크기의 1 행렬
```




    array([[1., 1., 1., 1.],
           [1., 1., 1., 1.],
           [1., 1., 1., 1.]])



`random()`은 선언하고 싶은 배열의 크기를 입력하여 0 이상 1 미만의 랜덤 값을 갖는 배열을 선언합니다.


```python
np.random.random((2,3)) # (2,3) 크기의 랜덤 행렬
```




    array([[0.29271583, 0.92294805, 0.46969237],
           [0.52926843, 0.81985309, 0.37042905]])



 

### 2. 배열 정보 확인하기

#### shape, size

선언된 numpy 배열은 어떤 크기인지 `.shape`와 `.size`를 통하여 확인할 수 있습니다.

`shape`는 배열의 row와 column의 크기를 출력하고 `size`는 배열의 성분들 총 개수를 출력합니다.


```python
c = np.array([[1,2,3],[4,5,6]])
c.shape
```




    (2, 3)




```python
c.size
```




    6



#### dtype

배열의 성분들 타입을 알기 위해서는 `.dtype`을 사용합니다.


```python
c.dtype
```




    dtype('int64')



#### 성분 확인

마지막으로 배열의 인덱스를 사용하여 해당 성분을 확인하는 방법에 대해서 알아봅시다. 


```python
c[0,0]
```




    1




```python
c[1,2]
```




    6



위 예시처럼 numpy 배열에 `[]`안에 해당 인덱스를 넣으면 해당 성분을 출력합니다.

여기서 중요한 점은 배열의 인덱스는 0부터 시작이라는 것을 잊지 말아야 합니다.

 

### 3. 배열 형태 변경하기

#### reshape

`reshape` 함수를 통하여 배열의 형태를 변경할 수 있습니다.

아래 예처럼 변경하고 싶은 배열의 형태를 입력하여 배열의 구조를 변경할 수 있습니다.


```python
a = np.array([1,2,3,4])
a = a.reshape((2, 2)) # 원래 a의 size와 변경할 a의 size는 같아야 함
# a = np.reshape(a,(2,2)) # 이와 같은 방법으로도 사용 가능
a
```




    array([[1, 2],
           [3, 4]])



변경된 배열의 `shape`와 `size`를 확인해보겠습니다.


```python
a.shape
```




    (2, 2)




```python
a.size
```




    4



이전에 (4,)였던 배열의 shape이 바로 위에서 설정한 대로 (2,2)로 변경된 것을 확인할 수 있습니다. 

그러나, 개수를 변경한 것은 아니기 때문에 size를 출력하였을 때는 동일한 결과가 출력됩니다.

만약 row의 개수에 상관없이 column의 수를 고정하고 싶다면 row 크기를 입력하는 인자에 -1을 입력합니다.


```python
a_col = a.reshape((-1,1))
a_col
```




    array([[1],
           [2],
           [3],
           [4]])




```python
a_col.shape
```




    (4, 1)



반대로 row를 고정해야 한다면 column 입력에 -1을 설정합니다.


```python
a_row = a_col.reshape((2,-1))
a_row
```




    array([[1, 2],
           [3, 4]])




```python
a_row.shape
```




    (2, 2)



 

### 4. 배열 자르고 붙이기

데이터를 다루다 보면 필요에 따라 배열의 특정 벡터를 잘라내거나 합쳐야 하는 상황이 자주 발생합니다.

#### 배열 자르기

배열을 자를 때는 배열의 인덱스 정보를 활용하여 자를 수 있습니다.

아래 예를 보며 이해해봅시다.


```python
a = np.array([[1,2,3],[4,5,6]]) # (2,3) 크기의 행렬 a 선언
a
```




    array([[1, 2, 3],
           [4, 5, 6]])



원래 행렬에서의 column 벡터를 뽑고 싶을 때 row 인덱스를 입력하는 부분에는 `:`, column 인덱스를 입력하는 부분에는 해당 column 인덱스를 입력합니다.


```python
a[:,0] # column 0번째 행 출력
```




    array([1, 4])




```python
a[:,-1] # 마지막 column [-1]행 출력
```




    array([3, 6])



원래 행렬에서의 row 벡터를 뽑고 싶을 때 column 인덱스를 입력하는 부분에는 `:`, row 인덱스를 입력하는 부분에는 해당 row 인덱스를 입력합니다


```python
a[1,:] # row 벡터로 자르기
```




    array([4, 5, 6])




```python
a[-1,:] # 마지막 row 벡터로 자르기
```




    array([4, 5, 6])



 

`배열[시작값:도착값,간격]`을 이용하여 배열의 일부를 잘라 표시할 수 있습니다.

아래 예를 통하여 이해해 봅시다.


```python
a = np.array([[1,2,3,4,5,6],[7,8,9,10,11,12]]) # (2,6) 크기의 행렬 a 선언
a
```




    array([[ 1,  2,  3,  4,  5,  6],
           [ 7,  8,  9, 10, 11, 12]])



`배열[시작값:]`은 `시작값` 인덱스를 시작으로 `배열의 마지막 인덱스`까지의 배열을 표시합니다.


```python
a[:,4:]
```




    array([[ 5,  6],
           [11, 12]])



`도착값`은 마지막 인덱스 값보다 1이 큽니다. 따라서 column 벡터의 크기가 6인 a배열의 `도착값`으로 6을 입력하면 5번 인덱스를 의미하게 됩니다.


```python
a[:,3:6]
```




    array([[ 4,  5,  6],
           [10, 11, 12]])




```python
a[:,2:-1]
```




    array([[ 3,  4,  5],
           [ 9, 10, 11]])



`-1`은 마지막 인덱스를 의미하기에 4번 인덱스까지를 출력합니다.


```python
a[:,0:3:2] 
```




    array([[1, 3],
           [7, 9]])



간격이 2이기에 0번, 2번 인덱스만을 표시합니다. 

 

#### 배열 붙이기

이번에 배열을 붙여 보겠습니다. 

배열을 붙이는 경우 붙이려는 배열들의 크기에 주의해야 합니다. 아래 예를 보며 이해해 봅시다.


```python
a = np.array([[1,2,3],[4,5,6]]) # (2,3) 크기의 행렬 a 선언
b = np.array([[7,8,9],[10,11,12]]) # (2,3) 크기의 행렬 b 선언
print(a)
print("\n",b)
```

    [[1 2 3]
     [4 5 6]]
    
     [[ 7  8  9]
     [10 11 12]]


`r_`은 기존 배열에 추가되는 배열을 마지막 row 아래에 붙입니다.


```python
np.r_[a,b] # row 를 추가
```




    array([[ 1,  2,  3],
           [ 4,  5,  6],
           [ 7,  8,  9],
           [10, 11, 12]])



`r_`와 같은 함수로 `concatenate((배열1,배열2), axis=0)`를 사용할 수 있습니다. 다만 배열1과 배열2의 차원은 같아야 합니다.


```python
np.concatenate((a,b), axis=0) # 0은 row 를 의미함
```




    array([[ 1,  2,  3],
           [ 4,  5,  6],
           [ 7,  8,  9],
           [10, 11, 12]])



`c_`은 기존 배열에 추가되는 배열을 마지막 column의 오른쪽에 붙입니다.


```python
np.c_[a,b] # column 을 추가
```

`c_`와 같은 함수로 `concatenate((배열1,배열2), axis=1)`를 사용할 수 있습니다. 다만 배열1과 배열2의 차원은 같아야 합니다.


```python
np.concatenate((a,b), axis=1) # 1은 column 을 의미함
```

 

### 5. 배열 연산

numpy 배열 연산은 기본적인 연산 기호(+,-,*)에 맞게 연산이 됩니다.

다만 벡터의 inner product나 행렬곱과 같은 특수한 연산은 특정 함수를 사용하여 수행합니다.

이 부분은 `머신러닝을 위한 수학`에서 자세히 다루겠습니다.

numpy 배열을 덧셈과 뺄셈은 `+,-`기호로 간단하게 수행 가능합니다.


```python
# 배열 덧셈
a = np.array([[1, 2, 3], [3, 2, 5]])
b = np.array([[-1, 3, 5], [1, 4, 2]])
a+b
```


```python
# 배열 뺄셈
a-b
```

numpy 배열의 `*`연산은 같은 인덱스에 존재하는 성분끼리 곱한 형태를 출력합니다.


```python
# * 연산은 각 성분끼리 곱한 형태를 출력
a*b
```

numpy 배열의 `/`연산은 같은 인덱스에 존재하는 성분끼리 나눈 형태를 출력합니다.


```python
# / 연산은 각 성분끼리 나눈 형태를 출력
a/b 
# 각 원소의 형태가 정수형이므로, 나눗셈 연산에서 자리 버림 발생
```

---

<span style="color:rgb(120, 120, 120)">본 학습 자료를 포함한 사이트 내 모든 자료의 저작권은 엘리스에 있으며 외부로의 무단 복제, 배포 및 전송을 불허합니다.

Copyright @ elice all rights reserved</span>
