# Type System

각 언어는 각각의 type system을 갖고 있다.

## Strong Type vs Weak Type

언어가 올바르지 않은 type 정보를 가진 program을 실행하는 것을 허용하는 지 여부를 나타낸다.

Strong type 언어는 type 검사를 통과하지 못한 program의 실행 자체를 막지만, weak type 언어는 runtime에 오류를 만나는 한이 있더라도 실행을 막지 않는다.

## Dynamic Type vs Static Type

Type system이 program의 type을 검사하는 시점이 언제인지에 따라 나눈다.

Static type 검사를 시행하는 언어는 runtime 이전에 시행한다.

Dynamic type 검사를 시행하는 언어는 runtime에 시행한다.

Static type 검사와 dynamic type 검사는 상호 배제적인 개념이 아니다. Static type 검사를 시행하는 언어가 runtime에도 어느 정도 type 검사를 시행하는 경우도 존재한다. Runtime에만 존재하는 정보를 통해서만 그 적법성을 판단할 수 있는 경우가 존재하기 때문이다. Type B가 type A의 sub type일 때, A type의 객체를 B type으로 형변환하는 downcasting이 그런 예이다.

### Gradual Typing

기존에 dynamic type 검사만을 수행하던 언어에 static type 검사를 도입하고자 하는 시도가 늘고 있다.

방대한 legacy code의 code base에 동시에 type 정보를 전부 적어야만 static type을 사용할 수 있다면 현실적으로 매우 어려울 것이다. 이런 상황을 피하기 위하여 gradual typing을 지원하는 언어가 많다.

Program 전체가 아닌 programmer가 명시한 일부 부분만 static type 검사를 거치게 하고 나머지 부분은 그대로 dynamic type 검사가 이루어지도록 하여, 말 그대로 점진적인 개선을 가능하게 하는 것이다.

## Explicit Type vs Implicit Type

Programmer가 직접 모든 값 또는 변수가 어떤 type에 속하는지 명시하는 type 선언 방식이 explicit type 선언 방식이다.

이미 type이 알려진 값, 변수, method 등의 정보를 이용해 code의 type 정보를 추론해내는 방식이 implicit type 선언 방식이다.
