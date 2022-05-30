# 220530

# Inheritance
* "Is a"
# Access specifier
* 상속 받을 때 접근자를 통해 상위 객체의 멤버 변수나 멤버 메소드에 접근을 제한할 수 있음
# Composition
* "Has a"
<!--more-->

# Inheritance
* "Is a"
* 객체 지향의 토대가 되는 상속(inheritance)
* 상위 객체의 메소드와 변수 등을 상속 받은 하위 객체가 사용 가능
* 하위 객체는 상위 객체에 없는 메소드와 변수 등을 추가로 정의해 좀 더 구체적인 구현체를 만들 수 있음
* 상위 객체는 하위 객체들을 추상화 한 구현체
* 접근자(access specifier)를 통해 멤버 변수나 멤버 메소드에 접근을 제한하여 캡슐화(encapsulation)

# Access specifier
* 상속 받을 때 접근자를 통해 상위 객체의 멤버 변수나 멤버 메소드에 접근을 제한할 수 있음
* Public: 상속 받은 상위 객체의 public or protected 멤버 변수 및 멤버 메소드에 하위 객체가 접근 가능
* Protect: 상속 받은 상위 객체의 public or protected 멤버 변수 및 멤버 메소드에 하위 객체의 protected 멤버로 접근자가 정해짐
* Private: 상속 받은 상위 객체의 public or protected 멤버 변수 및 멤버 메소드에 하위 객체의 private 멤버로 접근자가 정해짐

# Composition
* "Has a"
* 상속을 받는 것이 아닌 다른 객체를 멤버로 받아 오는 것

