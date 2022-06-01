# 220602


<!--more-->
# Udacity
## Multiple Inheritance
* ["Use multiple inheritance to represent multiple distinct interfaces"](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c135-use-multiple-inheritance-to-represent-multiple-distinct-interfaces)
* ["Use multiple inheritance to represent the union of implementation attributes"](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c136-use-multiple-inheritance-to-represent-the-union-of-implementation-attributes)
* Diamond Problem : 하나의 클래스가 두개의 base class로 부터 상속받고, 이 두개의 base class들은 동일한 추상 클래스로부터 상속을 받았다면, 충돌이 생긴다.
	* e.g.
	```cpp
	class Vehicle {
	public:
	    virtual string Move() const = 0;
	};
	
	class Boat : public Vehicle{
	    string Move() const;
	}; 
	class Car : public Vehicle {
	    string Move() const;
	};
	
	class AmphibiousCar : public Boat, public Car{
	    
	};
	
	int main(){
	    AmphibiousCar ab_car;
	    ab_car.move(); // Which is inherited?
	    return 0;
	}
	
## Generic Programming
* `template`을 사용하여 다양한 타입에 대응할 수 있도록 만드는 것을 **generic programming**
* 대표적으로 STL의 `vector`
### Template
* `template` 은 타입을 파라미터처럼 사용하여 다양한 데이터 타입에 대한 연산을 하나로 구현할 수 있음
```cpp
template <typename Type> Type Sum(Type a, Type b) {return a + b;}
```
* 실습
```cpp
#include <assert.h>

// TODO: Create a generic function Product that multiplies two parameters
template<typename T>
T Product(T a, T b) {return a * b;}

int main() { 
  assert(Product<int>(10, 2) == 20); 
}
```
* 예제 : 비교 연산자
```cpp
#include <assert.h>

// TODO: Declare a generic, templatized function Max()
template<typename T>
T Max(T a, T b) {return a > b ? a : b;}

int main() { 
  assert(Max(10, 50) == 50);
  assert(Max(5.7, 1.436246) == 5.7);
}
```


