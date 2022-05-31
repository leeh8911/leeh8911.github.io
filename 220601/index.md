# 220601


<!--more-->

# Polymorphism: overloading (review)
* 이전 강의에서 마저 듣지 못했던 나머지 내용 (코드 실습)
```cpp
#include <iostream>

class Human {};
class Animal {};
class Dog {};

// TODO: Write hello() function
void hello() { std::cout << "Hello, World!\n"; }

// TODO: Overload hello() three times
void hello(Human human) { std::cout << "Hello, Human!\n"; }
void hello(Animal animal) { std::cout << "Hello, Animal!\n"; }
void hello(Dog dog) { std::cout << "Hello, Dog!\n"; }

// TODO: Call hello() from main()
int main()
{
    hello();
    hello(Human());
    hello(Animal());
    hello(Dog());
}
```

# Polymorphism: operator
* ASCII table에 정의된 연산자를 선택해 새로운 연산 집합의 규칙을 정할 수 있음 
```cpp
// Example of '*'(plus) operator overloading!
Complex operator+(const Complex& addend) {
  //...logic to add complex numbers
}
```

* operator overloading, <+,-,/,*> + <++, --, +=, -=, *=, /=>, <==, <,>,<=,>=,!=>, ... 등등
* 실습 코드
```cpp
#include <assert.h>

class Point {
public:
    Point(int x, int y) : x(x), y(y){}
    
    int x;
    int y;
    
    Point operator+(const Point& p2){ return Point(x+p2.x, y+p2.y);}
    
};

int main() {
  Point p1(10, 5), p2(2, 4);
  Point p3 = p1 + p2; // An example call to "operator +";
  assert(p3.x == p1.x + p2.x);
  assert(p3.y == p1.y + p2.y);
}
```

# Virtual Functions
* `virtual return_t foo(input_t vars);`
* virtual function은 다형성을 위한 특징
* virtual function은 인터페이스를 위해 사용됨
* pure virtual function `virtual return_t foo(input_t vars); = 0`
```cpp
class Animal {
	virtual void Talk() const = 0;
};
```
* virtual function이 있는 클래스를 상속 받으면 해당 virtual function을 구현해야 함
* virtual function이 있는 클래스는 인스턴스를 만들 수 없음
* 실습 코드
```cpp
// Example solution for Shape inheritance
#include <assert.h>
#include <cmath>

// TODO: Define pi
const double pi = 3.14159;

// TODO: Define the abstract class Shape
class Shape{
  // TODO: Define public virtual functions Area() and Perimeter()
  // TODO: Append the declarations with = 0 to specify pure virtual functions
public:
    virtual double Area(void) const = 0;
    virtual double Perimeter(void) const = 0;
};

class Rectangle : public Shape{
public:
    Rectangle(int width, int height) : width(width), height(height) {};
    double Area(void) const { return width * height; }
    double Perimeter(void) const { return 2 * (width + height); }
private:
    int width;
    int height;    
};

class Circle : public Shape {
public:
    Circle(int radius) : radius(radius) {};
    
    double Area(void) const { return radius * radius * pi; }
    double Perimeter(void) const { return 2 * pi * radius; }
private:
    int radius;
};

// Test in main()
int main() {
  double epsilon = 0.1; // useful for floating point equality

  // Test circle
  Circle circle(12.31);
  assert(abs(circle.Perimeter() - 77.35) < epsilon);
  assert(abs(circle.Area() - 476.06) < epsilon);

  // Test rectangle
  Rectangle rectangle(10, 6);
  assert(rectangle.Perimeter() == 32);
  assert(rectangle.Area() == 60);
}
```

# Overriding


