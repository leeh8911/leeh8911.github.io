# 220621

* Copy semantics
<!--more-->
# Udacity
## Copy semantics
* 리소스 관리 (다중 스레드 락, 파일, 네트워크, 데이터베이스 연결 등)
* 리소스에 대한 엑세스는 종종 포인터로 다뤄짐
* 사용이 종료되면 해제해서 다른 사람이 재사용 할 수 있도록 해야 함
* RAII (Resource Acquisition is Initialization, 자원 획득은 초기화)
* 멤버 변수 중 포인터가 있는 클래스의 경우 기본 복사 생성자가 복사할 때 포인터 변수에 대해서는 얕은 복사가 수행되서 문제가 발생할 수 있음
* 얕은 복사 : 변수의 위치만을 복사해옴
* No copying policy : 가장 간단한 정책은 모든 클래스 인스턴스의 복사와 할당을 금지
	1. 복사 생성자를 private으로 만드는 것
	2. `NoCopyClass2(const NoCopyClass2 &) = delete;`
* Exclusive ownership policy : 객체에 대한 소유권은 하나만!
	1. 객체에 대한 복사를 수행하면 해당 객체가 소유한 포인터들의 소유권을 복사 된 객체로 옮겨줌 (복사 당한 객체에게는 `nullptr`

