# Java

### Static vs Non Static
<details>
<summary>static과 non static의 차이</summary>

<br>

<div>
non static은 클래스의 각 객체마다 별도로 존재하며 인스턴스 변수라고 부릅니다.
static은 클래스당 하나만 생성되며 클래스의 모든 객체들에게 공유됩니다.
</div>

#### Static 키워드
* static 키워드는 특정 클래스의 동일한 변수나 메소드를 고융하는 데 사용됩니다.
* 인스턴스가 아닌 클래스에 속하며 클래스의 모든 인스턴스에 대해 동일한 변수, 메소드에 사용할 수 있습니다.

#### Static 키워드 특징
* 공유 메모리 할당
  * 정적 변수와 메소드는 프로그램 실행 중 한번만 메모리 공간에 할당됩니다.
* 객체 없이 접근 가능
* 비정적 멤버 접근 불가
  * 클래스의 특정 객체와 연결되어 있지 않으므로 클래스의 non-static 멤버에 접근할 수 없습니다.
* 오버로딩 될 수 있지만 오버라이딩 불가능
  * static 메소드는 컴파일 시점에 메모리에 올라가 클래스에 종속적이기 때문에 상속되지 않습니다.

#### 주의점
* static 변수는 모든 객체에서 공유되므로, 변경 가능한 데이터는 static 변수보다는 인스턴스 변수로 선언하는 것이 좋습니다.
* 또한 static 변수는 클래스가 로딩될 때 초기화되므로 다른 static 변수의 값을 사용하려면 해당 변수가 먼저 초기화 되어 있어야 합니다.
</details>

### Exception

<details>
<summary>Exception이란?</summary>

<br>

<div>
프로그램 실행 중에 발생하는 이벤트로 프로그램 로직의 흐름을 방해하는 오류를 말합니다.
예외에는 컴파일 시점에 탐지되는 Checked Exception과 런타인 시점에 탐지되는 UnCheckedException이 있습니다.
</div>
</details>

<br>

<details>
<summary>Error와의 차이</summary>

<br>

<div>
Error는 복구될 수 없는 심각한 문제를 의미하며 개발자가 예측하여 방지할 수 없는 문제입니다.
메모리 부족이나 스택 오버플로우 같은 문제가 여기에 해당합니다.

Exception은 수습이 가능한 문제로 여러 방법을 통해 방지할 수 있습니다.
</div>
</details>

<br>

<details>
<summary>Exception Handling</summary>

<br>

<div>
예외 처리란 개발자가 예기치 못한 예외의 발생에 미리 대처하는 코드를 작성하는 것입니다.
동작하고 있는 프로그램의 비정상적인 종료를 막는 것이 목적입니다.
</div>

#### Try - catch 

* try
  * 예외를 발생시킬 수 있는 코드를 포함한 블록.
* catch
  * try 문에서 예외가 발생할 경우 예외를 처리하기 위한 블록.
* finally
  * 예외 발생 여부와 상관없이 항상 실행되는 코드 블록

#### throws

* 임의적으로 예외를 발생시킬 때 사용한다.
* 적절한 메시지를 인자로 전달해 로그를 기록할 수 있다.

#### method 예외 선언
* 메소드 선언부에 예외를 명시하여 메소드를 호출한 쪽으로 예외를 전달한다.

```java
int method() throws Exception {...}
```

#### try with resource
* AutoClosable을 구현한 객체에 대해서 예외 발생 여부와 상관없이 자원을 close 할 수 있다.

```java
try (Scanner scanner = new Scanner(...)) {
        ...
}
```
</details>

<br>

<details>
<summary>Exception 구분</summary>

<br>

<div>
Checked Exception과 Unchecked Exception으로 구분 할 수 있습니다.
Checked Exception은 컴파일 시점에 탐지되며 RuntimeException이 아닌 Exception의 하위 클래스입니다.
반드시 예외처리를 해야하는 예외입니다. ClassNotFoundException, FileNotFoundException 등이 있습니다.

<br>

Unchecked Exception은 런타인 시점에 탐지되며 RuntimeException의 하위 클래스입니다.
예외처리를 강제하지 않습니다. IllegalArgumentException, NullPointerException, IndexOutOfBoundsException 등이 있습니다.
</div>
</details>

### Optional

<details>
<summary>Optional</summary>

<br>

<div>
Optional은 Java에서 Return값이 없을수도 있음을 의미합니다.
Null이 들어갈 수 있는 값을 감싸는 Wrapper Class입니다.
Optional을 통해 NullPointerException이 발생하지 않도록 할 수 있습니다.
</div>

#### 주의 사항 

1. Optional의 return 값에 null을 사용하지 말 것
   * Null을 방지하려고 사용하는 Optional의 사용 목적에 어긋난다.
   * 내부 값을 null로 초기화한 싱글톤 객체인 Optional.empty()를 사용하자.
2. Optional을 필드, 메소드 인자, 컬렉션, 맵의 키에 사용하지 말 것
   * Optional이란 반환값이 없을 수 있다는 것을 의미하므로 사용 목적에 어긋남.
   * Collection에서는 빈 컬렉션을 반환할 수 있으므로 불필요한 비용을 줄일 수 있다.
3. Primitive Type에 Optional을 사용하기보다 OptionalInt, OptionalLong, OptionalDouble의 사용을 고려하자.
   * Optional로 사용할 때 Boxing, UnBoxing 과정을 통해 오버헤드가 발생한다.
   * wrapper 클래스가 아닌 primitive type을 내부 필드로 갖기 때문에 불필요한 오버헤디를 줄일 수 있다.
</details>

<br>

<details>
<summary>Optional 장단점</summary>

<br>

<div>
Optional은 Null을 직접 다루지 않아도 되며 Null Check를 줄여준다는 장점이 있습니다.
또한 해당 값이 없을수도 있다는 것을 직접적으로 명시할 수 있습니다.

<br>

단점으로는 값의 여부를 확인하지 않을 경우 NullPointerException이 아닌 NoSuchElementException이 발생할 수 있습니다.
또한 Wrapper 클래스로 감싸기 때문에 Optionanl 객체를 저장하고 접근하는 Overhead가 증가합니다.
</div>
</details>

### Serialization

<details>
<summary>직렬화</summary>

</details>

