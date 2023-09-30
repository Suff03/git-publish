tags : #python 

---

판다스는 [[Python]]의 데이터 분석 라이브러리이다. R에서 사용되던 `data.frame`구조를 본뜬 `DataFrame`이라는 구조를 사용한다. 파이썬이라는 접근성이 좋은 언어 기반으로 동작하기 때문에 데이터 분석을 파이썬으로 입문하는 사람들이 필수적으로 사용하는 라이브러리가 되었다. 주요 코드는 Python이나 C로 작성되었다.

##### Import
```python
import pandas as pd
```

##### Series, DataFrame
![[Pasted image 20230917153841.png]]
`Series`는 [[NumPy]]에서 제공하는 1차원 배열과 비슷하지만, 각 데이터의 의미를 표시하는 `index`를 붙일 수 있다. 데이터 자체는 `value`라고 한다.

`DataFrame`은 `Series`들을 하나의 열로 취급한 집합이다. 2차원 행렬 데이터에 `index`를 붙인 것과 같다. `row index`, `column index`가 있다. 데이터를 표의 형태로 처리한다. RDB 환경에서 SQL로 테이블을 컨트롤할 수 있는 수준의 기능들이 상당 부분 구현되있다.

ndarray는 하나의 data type을 가진다. 즉, List와 달리 Dynamic typing이 지원되지 않는다.

판다스의 큰 장점인 라벨링을 활용할 수 있다.

```python
df = pd.DataFrame([[3, 2, 5], [10, 0 ,2], [6, 5, 3]], index = ["이성계", "김유신", "이순신"], columns=["사과", "자두", "포도"])
s1 = df["사과"]
```

`NumPy`기반으로 제작되었기 때문에 `df.mean()`, `df1.sum()`등을 사용 가능하다.

##### Indexing, Slicing
![[Pasted image 20230917154532.png]]
기존의 Python과 비슷하다.
```python
df[] -> [] columns 추출..
df.loc[index 이름, columns 이름] # 이름
df.iloc[index 번호, columns 번호] # 번호
df.drop("D", axis=1) # Default = 0
```
![[Pasted image 20230917154834.png]]
axis는 이를 참조하면 된다.

만약 B, D, E, F 열과 가, 나, 다 행을 추출하고 싶다면.. (A ~ F 열, 가 ~ 마 행의 데이터)
```python
df.iloc[:3, 1:].drop("C", axis=1)
```

##### Sorting
`sort_values`로 값을 기준으로 정렬할 수 있다. `ascending`이 True일 때 오름차순으로 정렬한다.
```python
df.sort_values(["수학", "나이"], ascending=[0,1])
```

##### Broadcasting
`Broadcasting`은 기본적으로 `NumPy`의 `Broadcasting`과 비슷하다. 그러나 몇 가지 차이점이 있다. `Pandas`에서는 라벨링이 중요하다. 라벨이 맞지 않으면 없는 부분으로 `NaN`값을 채운다.

`DataFrame`과 `Series`의 연산을 `Broadcasting`이라 칭할 수 있다.

##### Boolean Indexing
`bool` 자료형을 이용하여 인덱싱을 활용하는 기법.
fill_value : 없는 값을 0으로 채우고 연산하라

* isnull()
	NaN일시 True
```python
df.loc[(~df["과학"].isnull()) | (df["수학"] > 90)]
```

* isin()
	소속 여부를 `boolean`으로 반환
```python
df.loc[df["소속"].isin(["문예부", "과학부", "다도부"])]
```

##### Index & Columns
* df.index, df.columns
```python
list(df.index), df.columns
>>> [0, 1, 2, 3], Index(['종목', 'A팀', 'B팀', 'C팀', 'D팀', '분류'], dtype='object')
```

* df.set_index()
	`columns`를 이용해 `index`를 설정한다.
```python
df.set_index(["분류", "종목"])
```

* df.reset_index()
	`index`를 리셋 시키는데 사용된다.
```python
df.reset_index(drop=True)
```

* df.reindex()
	기존의 `index`를 새로운 `index`로 덮어 씌우는데 사용된다.
```python
df.reindex(columns=["A팀", "B팀", "A팀", "E팀"], fill_value=0)
```

* df.sort_index()
	`axis`를 기준으로 `index`를 정렬한다.
```python
df.sort_index(axis=1)
```

##### Pivot & Pivot Table
![[Pasted image 20230918145927.png]]
`Pandas`를 이용해 유용한 데이터 분석을 다루려면 필히 알아야 하는 기능이다.

`Pivot Table`의 가장 큰 장점은 **데이터를 내가 원하는 대로 표시하고 분석할 수 있다는 장점**이다. 많은 양의 데이터에서 필요한 자료만을 뽑아 새로운 `DataFrame`을 작성할 수 있다.

* df.pivot_table()
	집계 함수 `aggfunc`이 필요하다.
```python
df.pivot_table("점수", index="반", columns="성별", aggfunc="mean")
```

* df.pivot()
	집계 함수 `aggfunc`이 필요하지 않다. 즉, `values`가 숫자형일 필요가 없다. (values=)을 꼭 적어주어야 한다.
```python
df.pivot(values="이름", index="반", columns="반등수")
```

##### Unpivot
![[Pasted image 20230918151101.png]]
`Pivot`의 반댓말이다. 피벗된 자료를 다시 재구성 하는 과정이다.

그럼 `Unpivot`을 왜 하는 것일까?
피벗된 데이터 자료를 다른 방향으로 구성하고 싶을 때 어려움이 존재한다. 따라서 피벗된 데이터를 언피벗하고 다시 피벗하는 과정을 통해 데이터를 다방향으로 재구성한다.

* df.stack()으로 언피벗하기
	1. set_index()로 언피벗하지 않을 열을 `index`로 변환한다.
	2. stack()으로 언피벗된 `Series`를 만들고, reset_index()로 언피벗된 `DataFrame`을 만든다.
	3. df.columns, 혹은 rename으로 열들의 이름을 바꾼다.

* df.melt()로 언피벗하기
	id_vars=를 적어주어야 한다. 파라미터를 이용해 이름을 바꿀 수 있다.
```python
df4.melt(id_vars=["반", "성별", "업체"], var_name="제품", value_name="수량")
```
