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