# 220701


<!--more-->
# Udacity
## Transferring Ownership
* Smart pointe를 사용할 때 함수의 반환값은 return-by-value
	* 일반적으로 값비싼 복사 프로세스로 인한 오버헤드를 smart pointer의 move semantic이 완화해줌
	* C++17부터 컴파일러가 return-by-value와 관련된 복사를 피하기 위해 Return Value Optimization을 사용
	* 값으로 shared_ptr이 반환될 때 reference_count는 적절히 증가가 보장 (포인터나 참조의 경우 X)
* Best-Practices for Passing Smart Pointer
```cpp
void f(object*);				//(a)
void f(object&);				//(b)
void f(unique_ptr<object>);		//(c)
void f(unique_ptr<object>&);	//(d)
void f(shared_ptr<object>);		//(e)
void f(shared_ptr<object>&);	//(f)
```

* 선호되는 방법
```cpp
void f(object*);				//(a)
void f(object&);				//(b)
```
	* 위의 (a), (b)와 같이 구현 시 구현체를 호출 할 때 lifetime 규칙에 대해 고민할 필요가 없음
	* 객체의 수명이 함수 매개변수의 수명을 초과할 것이라고 가정할 수 있는 객체를 관찰 가능( 동시성의 경우 X)
	* `*`와 `&` 중 어떤 것이 더 적절한지는 목적 여부
* 객체 구멍
```cpp
void f(unique_ptr<object>);
```
	* 함수가 객체의 소유권을 가져가도록 함
	* const와 함께 사용되지 않음

* 입력과 출력 1
```cpp
void f(unique_ptr<object>&);	//(d)
```
	* 이 경우 `unique_ptr`(주어진 객체일 필요는 없음) 수정하거나 호출자의 맥락에서 재사용 하고자 할 때 사용
	* 이러한 호출 구조를 통해 스마트 포인터를 수정할 수 있는 상태임을 나타냄
	* `const`를 사용한 호출 구조는 추천되지 않음 (내부에서 수정할 수 없게 되므로)

