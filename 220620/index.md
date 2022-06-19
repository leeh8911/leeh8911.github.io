# 220620

* Using malloc and free
* Using new and delete
* Typical memory management problems
<!--more-->
# Udacity
## Using malloc and free
* `malloc` 과 `calloc`은 모두 `stdlib.h`나 `malloc.h`에 포함된 함수
* `pointer_name = (cast-type*) malloc(size)` : 하나의 거대한 메모리 블럭을 동적할당 해줌. `malloc`의 리턴값은 `void*`이기 때문에 원하는 타입으로 캐스팅 해줘야함
* `pointer_name = (cast-type*) calloc(num_elems, size_elem)` : 여러개의 메모리 블럭을 동적할당 해줌. 모든 동적 할당된 메모리의 값은 0으로 초기화됨. `malloc`과 마찬가지로 `void*`로 출력
## Using new and delete
* `malloc`과 `free`는 C에 포함된 함수
* `new`와 `delete`는 C++에서 소개된 연산자로서 객체지향에 대응
* `malloc`으로 객체의 메모리 공간을 할당할 때, 생성자를 불러올 수 없음 (`new`는 가능)
* 소멸자에 대해서도 마찬가지로 `free`는 안되지만, `delete`는 가능함
* placement `new`: 
```cpp
void *memory = malloc(sizeof(MyClass));
MyClass *object = new (memory) MyClass;
```
* `new (memory)`문법이 placement `new`
* 원래 `new`와는 다른 점은 메모리 할당이 안됨
```cpp
object->~MyClass();
free(memory);
```
* `new`와 `delete`는 연산자로 overloading이 가능함
```cpp
void* operator new(size_t size);
void operator delete(void*);
```

## Typical memory management problems
* C++의 최고의 장점은 프로그래머가 직접 자원을 유연하게 제어 가능
	1. 메모리 유출(memory leaks): 런타임 도중 생성된 자원들을 적절히 해제해주지 않으면 발생
	2. 버퍼 오버런(buffer overrun): 할당된 메모리 공간보다 많은 자원을 사용하고자 하면 발생
	```cpp
	char str[5];
	strcpy(str, "BufferOverrun");
	printf("%s", str);
	```
	3. 초기화 되지 않은 메모리(uninitialized memory): 컴파일러에 따라 대부분은 0으로 메모리가 알아서 초기화 되지만, 메모리 할당 할 때 적절한 값으로 초기화 하지 않으면 발생
	4. 부적절한 할당자-해제자 연결(incorrect pairing of allocation and deallocation): `malloc()` -> `free()` : `new` ->> `delete`
	5. 검증되지 않은 메모리 접근(invalid memory access): 이미 해제된 메모리에 접근하려 할 때 발생

