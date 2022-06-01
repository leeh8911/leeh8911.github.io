# 220531

## Polymorphism
* 다형성(polymorphism)은 "수 많은 형태를 가정"했다는 의미
## Friend
* `friend` 클래스는 상속의 대안

<!--more-->

## Friend
* `friend` 클래스는 상속의 대안
* 일반적인 상속과 달리 private 멤버에도 접근 가능

```cpp
class Heart {
private:
int rate{80};
friend class Human;
}

class Human {
public:
Heart heart;
void Exercise(){ heart.rate = 150;}
void HeartRate(){return heart.rate;}
};
```

## Polymorphism
* 다형성(polymorphism)은 "수 많은 형태를 가정"했다는 의미
* 다형성은 C++상에서 두가지 방법으로 구현: overloading & overriding
* Overloading 두가지 이상의 이름만 같고 다른 버전의 함수를 구현하는 것을 일컫음
* 이름만 같고 입력 인수는 다양한 함수들!


