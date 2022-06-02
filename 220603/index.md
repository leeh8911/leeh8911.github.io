# 220603


<!--more-->
#Udacity
## Deduction
* [deduction](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rt-deduce)
* **Deduction**은 객체를 생성할 때 타입을 명시하지 않으면 발생
* 예제 코드
```cpp
#include <assert.h>

// TODO: Declare a generic, templatized average function
template<typename T>
T average(T a, T b) {return (a + b) * 0.5; }

int main() { assert(average(2.0,5.0) == 3.5); }
```

## Exercise Class Template
```cpp 
#include <assert.h>
#include <string>
#include <sstream>

// TODO: Add the correct template specification
template<typename KeyType, typename ValueType>
class Mapping {
public:
  Mapping(KeyType key, ValueType value) : key(key), value(value) {}
  std::string Print() const {
    std::ostringstream stream;
    stream << key << ": " << value;
    return stream.str();
  }
  KeyType key;
  ValueType value;
};

// Test
int main() {
  Mapping<std::string, int> mapping("age", 20);
  assert(mapping.Print() == "age: 20");
}
```
## System Monitor Project!
* htop - Linux system monitor

## Style Code (C++)
* clang-format

