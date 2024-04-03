# JAVA

## Reflection

<details>

<summary>Reflection 이란 ?</summary>
<p>

#### 생성자, 메서드, 필드 등 클래스에 대한 정보를 런타임에 알아낼 수 있는 기술

JVM은 클래스에 대한 정보를 클래스 로더를 통해 읽어와서, 해당 정보를 JVM 메모리에 저장

- 클래스에 대한 정보가 마치 거울에 투영된 모습과 닮아있어, 리플렉션 이라는 이름을 가지게 됨

</details>

<br>

<details>

<summary>Reflection 이 어디에 사용되나요 ?</summary>
<p>

### Annotation

- Reflection 을 사용하면, 클래스와 메서드에 어떤 어노테이션이 붙어 있는지 확인할 수 있음
- 어노테이션은 그 자체로는 아무 역할도 하지 않지만, Reflection 덕분에 Spring 에서 `@Component`, `@Bean` 과 같은 어노테이션을 프레임워크의 기능을 사용하기 위하여 사용할 수 있음

### JACKSON

- Spring 에서 JSON 을 Java의 Object 로 Mapping 할 때, Reflection 이 사용됨
- `@RequestBody` 가 대표적으로 Reflection 을 사용하는 Spring 어노테이션
- `@NoArgsConstructor` 를 통하여 객체를 생성하고, Reflection 을 통하여 내부 필드를 주입시킴

</details>

<br>