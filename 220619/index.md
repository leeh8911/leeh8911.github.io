# 220619

* Heap memory
* Using malloc and free
<!--more-->
# Udacity
## Heap memory
* 동적 할당에 사용되는 메모리 영역
* BSS와 Data segment 바로 위에 위치해 있음
* Stack은 높은 주소부터 낮은 주소로 확장되지만, Heap은 반대로 낮은 주소에서 높은 주소로 확장됨
* Heap 메모리의 특징
	1. Stack과 달리 scope를 벗어날 때 삭제되지 않고 남아있음
	2. Stack은 컴파일 단계에서 결정되지만, heap은 런타임 단계에서 결정됨
	3. Heap은 접근 가능한 메모리의 주소 공간의 크기에만 영향을 받음 (동적으로 할당된 변수를 해제 하는 것을 까먹으면, 메모리 누수라고 함)
	4. Stack과 달리 멀티 스래드상에서 공유될 수 있음
	5. Stack은 할당/삭제가 순차적으로 이루어져 메모리 공간을 효율적으로 사용할 수 있지만, Heap의 경우에는 그러지 못해 관리가 까다로움
* 메모리 파편화

## Using malloc and free
* 


