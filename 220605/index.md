# 220605


* Memory Utilization
<!--more-->
# Udacity
## Memory Utilization
* [Reference](https://www.thegeekdiary.com/understanding-proc-meminfo-file-analyzing-memory-utilization-in-linux/)
* `/proc` 은 가상의 파일 시스템
* `/proc/meminfo`는 비어있거나 사용중인 메모리의 양을 보고하기 위한 곳
* `cat /proc/meminfo`를 통해 획득한 정보들은 상위와 하위 통계 형태로 제공
* [Stack-over-flow (mem usage from meminfo like htop)](https://stackoverflow.com/questions/41224738/how-to-calculate-system-memory-usage-from-proc-meminfo-like-htop/41251290#41251290)
* `memory utilization`은 `MemTotal`에서 `MemFree` + `MemBuffers` + `Shmem` + `SReclaimable` 의 총 합을 뺀 것(?)


