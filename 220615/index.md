# 220615


<!--more-->
## Hungarian Algorithm
* [reference](https://en.wikipedia.org/wiki/Hungarian_algorithm)
* Step1 : 각 행(row)에서 가장 작은 원소로 해당 행의 요소를 모두 빼준다
* Step2 : 각 열(column)에서 가장 작은 원소로 해당 열의 요소를 모두 빼준다
* Step3 : 행렬에서 모든 0인 원소를 가능한 적은 행 그리고/또는 열을 마킹하여 덮어준다
* Step4 : 왼쪽에 있는 원소로부터 가장 작은 원소를 찾는다. 마킹되지 않은 원소로 이것을 빼주고, 그것을 두개의 선으로 덮인 모든 원소들을 더해준다. 할당이 가능할 때 까지 step3-4를 반복한다.

