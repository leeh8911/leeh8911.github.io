# 220627

* Resource Acquisition is Initialization
	* 자원의 획득과 해제:
	* 신뢰할 수 있는 자원 해제 문제
	* RAII to the rescue
* What is RAII
<!--more-->
# Udacity
## Resource Acquisition is Initialization
* 자원의 획득과 해제:
	1. `new` or `malloc`을 통한 메모리 할당을 하면, `delete` or `free`를 매치시켜줘야 함
	2. 파일이나 네트워크를 연결하였다면, 필요없어진 시점에 닫아야 함
	3. 동시성 보호를 위한 atomic operations, memory barriers, monitors, critical sections를 할당했다면, 다른 쓰레드에서 그것들을 가져가기 전에 해제해줘야 함
* 신뢰할 수 있는 자원 해제 문제
	* 일반적인 패턴: \[자원 획득\] -> \[자원 사용\] -> \[자원 해제\]
	* 일반적인 패턴의 문제: 
		1. 프로그램은 리소스 사용 중 예외를 throw할 수 있어 release지점에 도달하지 못할 수도 있음
		2. 해제될 수 있는 시점이 많아 프로그래머가 모든 상황을 추적할 수 없음
		3. 다시 해제하는 것을 잃어 버릴 수도 있음
* RAII to the rescue
	* RAII의 주된 아이디어는 객체 소유권과 정보 은닉에 관한 것
	* 클래스 관리에 할당과 해제를 숨겨 놓았기 때문에 개발자는 걱정할 필요가 없음
	* 직접 할당하지 않았다면, 직접 해제해줄 필요 없음
	* RAII는 클래스를 관리하며 자원을 보호해줌
	* `new` and `delete`와 같은 할당/해제를 코드의 표면에서 숨길 수 있음
	* 장점:
		1. 클래스의 소멸자를 사용하여 RAII 객체가 범위를 벗어날 때, 적절한 메모리 할당/해제와 같은 리소스 정리작업 수행
		2. 동적으로 할당된 객체의 소유권 및 수명 관리
		3. 동일한 객체 내에서 수행되는 리소스 획득 및 해제로 인한 캡슐화 및 정보 은닉 구현
	* 메모리 관리 관점에서의 RAII
		1. RAII 클래스의 생성자로 자원 할당
		2. RAII 클래스의 소멸자로 자원 해제
		3. RAII 클래스의 모든 인스턴스는 스택에 할당되어 개체 범위를 통해 수명을 안정적으로 제어
		
# Others
## What is RAII [blog](https://blog.seulgi.kim/2014/01/raii.html)
* C++에서 자주 쓰이는 idiom으로 자원의 안전한 사용을 위해 객체가 쓰이는 스코프를 벗어나면, 자원을 해제해주는 기법

