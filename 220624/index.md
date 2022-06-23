# 220624


* Copy Semantics
	* Exclusive copy class
	* Deep copy class
	* Shared copy class
* L-values and R-values
<!--more-->
# Udacity
## Copy Semantics
* Exclusive copy class
```cpp
class ExclusiveCopy {
 private:
	int* _myInt;
 public:
	ExclusiveCopy() {
		_myInt = (int*)malloc(sizeof(int));
	}
	~ExclusiveCopy() {
		if (_myInt != nullptr) {
			free(_myInt);
		}
	}
	ExclusiveCopy(ExclusiveCopy& source) {
		_myInt = source._myInt;
		source._myInt = nullptr;
	}
	ExclusiveCopy& operator=(ExclusiveCopy& source) {
		_myInt = source._myInt;
		source._myInt = nullptr;
		return *this;
	}
};
```
* 복사 생성이나 할당 연산 수행시 멤버 변수 중 포인터 변수의 소유권도 같이 넘겨줌 (같은 포인터를 여러 객체가 소유하게 되면, 누가 언제 해제하게 될지 알 수 없어 위험함)
* Deep copy class
```cpp
class DeepCopy {
 private:
	int *_myInt;

 public:
	DeepCopy() {
		_myInt = (int*)malloc(sizeof(int));
	}
	~DeepCopy() {
		if (_myInt != nullptr) {
			free(_myInt);
		}
	DeepCopy(DeepCopy& source) {
		_myInt = (int*)malloc(sizeof(int));	
		*_myInt = *source._myInt;
	}
	DeepCopy& operator=(DeepCopy& source) {
		_myInt = (int*)malloc(sizeof(int));
		*_myInt = *source._myInt;
		return *this;
	}
};
```
* 깊은 복사는 단순 주소값만 가져오는 것이 아니라, 값을 복사해옴
* 하지만 메모리 요구량이 증가하고, 데이터의 유일성은 잃어버리게 됨
* Shared copy class
```cppclass SharedCopy
{
private:
    int *_myInt;
    static int _cnt;

public:
    SharedCopy(int val);
    ~SharedCopy();
    SharedCopy(SharedCopy &source);
};

int SharedCopy::_cnt = 0;

SharedCopy::SharedCopy(int val)
{
    _myInt = (int *)malloc(sizeof(int));
    *_myInt = val;
    ++_cnt;
    std::cout << "resource allocated at address " << _myInt << std::endl;
}

SharedCopy::~SharedCopy()
{
    --_cnt;
    if (_cnt == 0)
    {
        free(_myInt);
        std::cout << "resource freed at address " << _myInt << std::endl;
    }
    else
    {
        std::cout << "instance at address " << this << " goes out of scope with _cnt = " << _cnt << std::endl;
    }
}

SharedCopy::SharedCopy(SharedCopy &source)
{
    _myInt = source._myInt;
    ++_cnt;
    std::cout << _cnt << " instances with handles to address " << _myInt << " with _myInt = " << *_myInt << std::endl;
}
```
* 얕은 복사와 유사하지만, 몇 번 복사가 되었는지 확인
* 추후 알아보게 될 `unique_ptr`의 아이디어

## L-values and R-values
* C+11부터 하나의 표현식은 5가지의 값을 갖음
```
Expression
|
+- glvalue
|		+- lvalue
|		|
|		+-xvalue
|		|
+- rvalue
		+- prvalue
```
* Lvalues: 
	* 접근 가능한 주소를 갖고 있음
	* 컴파일러의 평가에 따라 함수 또는 객체의 ID가 결정되는 식
* Prvalues:
	* 직접 접근이 가능한 주소를 갖고 있지 않음
	* 임시적인 표현식으로 객체의 초기화나 어떤 값에 대한 연산을 수행할 때 피연사자로 사용됨
* 단순함을 위해 Udacity 강좌에선 Prvalues를 rvalue라고 표현함
* `int i = 42; // lvalue = rvalue;`
* lvalue references
	* lvalue reference는 개체의 대체 이름으로 간주됨
	* `int i = 1, &j = i;` 라고 적으면, `j`는 `i`의 또 다른 이름
* rvalue references
	* rvalue의 경우 lvalue reference에 대입하면 컴파일 오류가 발생함
```cpp
void myFunction(int &val)
{
	std::cout << "val = " << val << std::endl;
}

int main()
{
	int j = 42;
	myFunction(j);

	myFunction(42);

	int k = 23; 
	myFunction(j+k);

	return 0; 
}
```
	* C++11부터는 rvalue reference라는 새로운 타입이 생김! (`&&`를 씀으로써 가능해짐)
	* 위의 코드에서 `int &val --> int &&val`로 바꾼다면 오히려 사용 가능했던 `j`에 대한 함수에서 에러가 발생하고, 나머지 두개에 대해서는 정상적으로 실행됨

