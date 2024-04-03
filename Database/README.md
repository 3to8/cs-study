# Database

### View

<details>
<summary>view란?</summary>

<br>

<div>
데이터베이스에 물리적으로 존재하지 않지만 하나 이상의 테이블로부터 유도된 가상의 테이블로
데이터의 논리적 독립성을 제공하는 데이터베이스 개체입니다.

뷰는 사용자 관점에서 실제 데이터가 저장된 테이블처럼 사용할 수 있습니다.
하지만 인텍스를 설정할 수 없고, 뷰의 정의를 변경할 수 없습니다.
기본키를 포함하고 정의할 경우, 삽입, 삭제, 갱신이 가능합니다.
</div>

* 생성 예시
```sql
CREATE VIEW OOO
AS
SELECT ...
```

* 삭제 예시
```sql
DROP VIEW OOO
```
</details>

### Transaction

<details>
<summary>트랜잭션이란?</summary>

<br>

<div>
트랜잭션은 데이터베이스의 상태를 변화시키는 기능을 수행하기 위한
작업의 단위 또는 한번에 모두 수행되어야 할 일련의 연산입니다.
</div>
</details>

<br>

<details>
<summary>트랜잭션 특징</summary>

<br>

<div>
트랜잭션은 ACID라는 특징이 있습니다.

하나의 트랜잭션은 모두 실행되거나 모두 취소되어야 한다는 Atomicity(원자성),
트랜잭션이 실행에 성공하면 항상 일관성 있는 DB 상태를 유지해야 한다는 Consistency(일관성),
여러 트랜잭션이 동시에 실행 되어도 다른 트랜잭션에 영향을 줄 수 없다는 Isolation(독립성),
커밋된 트랜잭션의 결과는 영구적으로 반영되어야 한다는 Durability(영속성)이 있습니다.

</div>
</details>

<br>

<details>
<summary>트랜잭션의 연산</summary>

<br>

<div>
트랜잭션의 작업에 대해서 Commit 연산과 Rollback 연산이 있습니다.

Commit 연산은 트랜잭션의 작업이 성공적으로 완료되어 데이터베이스에 트랜잭션의 결과를 반영하는 연산입니다.

Rollback 연산은 트랜잭션의 작업이 중간에 실패해 트랜잭션에서 수행한 작업을 되돌리는 연산입니다.
</div>
</details>

<br>

<details>
<summary>트랜잭션의 상태</summary>

<br>

<div>
트랜잭션은 Active, Partially Committed, Commited, Failed, Aborted라는 5개의 상태를 가집니다.
</div>

* Active
  * 트랜잭션이 작업을 수행중인 상태
* Partially Commmited
  * 트랜잭션의 마지막 연산이 끝나 Commit 연산이 실행되기 직전의 상태
* Committed
  * Commit 연산을 실행해 데이터베이스에 결과가 반영된 상태
* Failed
  * 트랜잭션의 작업이 수행중 실패한 상태
* Aborted
  * 트랜잭션 작업이 실패해 Rollback 연산을 실행해 이전 상태로 되돌아간 상태
</details>

<br>

<details>
<summary>트랜잭션 격리 레벨</summary>

<br>

<div>
Read UnCommitted, Read Committed, Repeatable Read, Serializable이 있습니다.
</div>

* Read UnCommitted
  * 다른 트랜잭션에서 커밋되지 않은 내용에 접근이 가능합니다.
  * Lock이 발생하지 않습니다.
  * Dirty Read, Non-Repeatable Read, Phantom Read가 발생할 가능성이 있습니다.

* Read Committed
  * 다른 트랜잭션에서 Commmitted 된 내용만 접근이 가능합니다.
  * Lock이 발생하지 않습니다.
  * Non-Repeatable Read, Phantom Read가 발생할 가능성이 있습니다. 

* Repeatable Read
  * 트랜잭션에서 검색중인 데이터는 다른 트랜잭션에서 수정, 삭제가 불가능합니다.
  * Phantom Read가 발생할 수 있습니다.

* Serializable
  * 트랜잭션이 검색중인 데이터는 다른 트랜잭션에서 수정, 삭제, 조회가 불가능합니다.
  * 모든 이상현상을 방지하지만 성능이 좋지 않습니다.
    
#### Dirty Read
* 다른 트랜잭션에 의해 수정됐지만 아직 Commit 되지 않은 데이터를 읽는 것을 말합니다.

#### Non-Repeatable Read
* 한 트랜잭션에서 여러번 조회할 때 결과가 다르게 나타나는 현상을 말합니다.

#### Phantom Read
* 한 트랜잭션에서 같은 쿼리를 두번 수행할 때 첫 쿼리에 없던 결과가 두 번째 쿼리에 나타나는 현상을 말합니다.
</details>