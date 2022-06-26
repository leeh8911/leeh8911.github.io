# 220626

* Move semantic
	* Rule of Tree: 메모리 관리를 위해 필요한 것
	* before C++11 SMART POINTER
* Resource Acquisition is initialization
	* `new`와 `delete`에 대한 문제점들
	* 스마트 포인터의 이점

<!--more-->
# Udacity
## Move semantic
* Rule of Tree: 메모리 관리를 위해 필요한 것
	1. Overloaded copy constructor
	2. Copy assignment operator
	3. Destructor
* before C++11 SMART POINTER

## Resource Acquisition is initialization
* `new`와 `delete`에 대한 문제점들
	1. 적절한 페어링이 필요 : `new`로 생성된 변수들은 적절한 시점에 `delete`해야 함. 그렇지 않으면 메모리 누수가 발생
	2. 올바른 연산 페어링 : `new`로 생성되면 `delete`으로, `new[]`로 생성되었으면 `delete[]`로 삭제 해야함. 그렇지 않으면 프로그램이 정의되지 않은 행동을 하게 됨
	3. 메모리의 소유권 : 리소스 할당/해제를 누가 담당하는지 알아야 함. 그렇지 않으면 잘못된 소유권을 갖고 있는 메모리를 해제함으로써 내부 작동에 방해가 됨
* 스마트 포인터의 이점:
	* 스마트 포인터는 C++에서 소개된 것으로 자동으로 메모리 관리를 도와줌 (더 이상 필요 없어진 포인터는 자동으로 해제 됨)
	* 스마트 포인터는 원본 포인터를 감싼 클래스로 `->`와 `*`연산을 overload 함
	* RAII (Resource Acquisition Is Initialization, 자원 획득 시 초기화)

