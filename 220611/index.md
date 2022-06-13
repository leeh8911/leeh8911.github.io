# 220611


<!--more-->
# C++
## Vector Operator `==`
```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```
* `left` 와 `right`의 요소 수가 같고, 개별 요소가 같으면 `true` 아니면 `false`를 반환
## Matrix multiplicity
* 행렬 곱 구현에 대한 방법들 비교
    1. baseline으로 OpenCV matrix mult 사용
    2. 가장 일반적인 행렬곱 방법
    3. 메모리 효율을 높이기 위해 두번째 행렬을 transpose 시켜서 사용(메모리 캐싱에서 이득을 보기 위함)
* Debug 에서는 
	* 2x2 의 경우에는 3 > 2 > 1 (3번 방법이 가장 빠름)
	* 10x10의 경우에는 1 > 3 > 2 (1번 방법이 가장 빠름)
	* 100x100의 경우에는 1 > 3 > 2 (1번 방법이 가장 빠름)
## Clang-format
```terminal
clang-format src/*.cpp -i
```
* 위의 예시처럼 하면 특정 폴더 내의 cpp파일만 포메팅 가능

