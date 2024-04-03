# Database

## Relation

<details>

<summary>Relation 이란?</summary>
<p>

Relation Scheme + Relation Instance 를 뜻함

</details>

<br>

<details>

<summary>Relation Scheme 란?</summary>
<p>

### 데이터베이스의 구조와 제약조건에 관한 전반적인 명세를 의미

```
학생(학번: 문자열, 이름: 문자열, 로그인: 문자열, 나이: 정수, 평점 평균: 실수)
```
- 학생 : 릴레이션 이름 (Relation name)
- 학번, 이름, 로그인, 나이, 평점 평균 : 속성 이름 (Field, Column, Attribute name)
- 문자열, 정수, 실수 : 도메인 이름 (Domain name)

### 도메인

- Attribute name + Type Constraint
- 하나의 Attribute 가 가질 수 있는 동일한 유형의 원자값들의 집합
- Relation Scheme 는 Relation Instance 의 각 Field 의 Domain 을 명세(Domain constraint)
- Programming Language 관점에서 Field의 Data type 을 의미

</details>

<br>

<details>

<summary>Relation Instance 란?</summary>
<p>

**Set of (Record, Tuple) ... (Record, Tuple) 의 집합**

### Tuple

- Relation Scheme 에 정의된 각 Attribute 로 정의되며, 하나의 Data 묶음을 의미
- Relation Instance 에서 각 Tuple 을 하나의 행(row) 으로 구성

### Cardinality

Relation Instance 안에 존재하는 Tuple 의 개수

### Degree

Relation Instance 안에 존재하는 Field(Attribute) 의 개수

### 특징

- Relation Instance 에서 Tuple 의 순서는 중요하지 않음 (튜플의 무순서)
- Domain 에 정의된 범위를 따라야 하는 Domain Constraint 에 따라, Field 에 존재할 수 있는 데이터의 값을 제한할 수 있음

</details>

<br>

<details>

<summary>Relation 의 특징 ?</summary>
<p>

### Tuple 의 유일성

하나의 Relation 에는 동일한 Tuple 이 존재할 수 없음

- 학생 Relation 에서 "학번" 이라는 Attribute 값이 각 Tuple 마다 다르므로, 각 Tuple 을 유일하게 구별할 수 있음
- 이처럼 Tuple 을 유일하게 구별(Tuple 의 유일성) 하기 위해 선정되는 속성(또는 속성들의 집합)을 키(Key) 라고 부름

### Tuple 의 무순서

데이터베이스는 위치가 아닌 내용으로 검색되므로, Tuple 의 순서는 중요하지 않음

### Attribute 의 무순서

Attribute 의 순서가 변경되어도, Relation Scheme 는 동일하므로 두 릴레이션은 같음

### Attribute 의 원자성 (Atomic)

모든 Attribute 값은 더는 분해할 수 없는 하나의 값, 즉 원자값만 가질 수 있음

- 하나의 Attribute 는 여러 개의 값, 즉 다중 값을 가질 수 없음

</details>

<br>