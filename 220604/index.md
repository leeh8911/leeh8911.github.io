# 220604


## System Data
## Processor Data
## Process Data

<!--more-->
# Udacity
## System Data
* Linux 수 많은 시스템 데이터를 `/proc` 디렉터리에 파일로 저장해두고 있음
* Operating System : `cat /etc/os-release`
* Kernel : `cat /proc/version`
* Memory Utilization : `cat /proc/meminfo`
* Total Processes : `cat /proc/stat`
* Up Time : `cat /proc/uptime`

## Processor Data
* Linux 는 프로세서 데이터를 `proc/stat`에 있는 파일에 저장
* 각 `cpu`에는 10개의 정수형 정보가 포함되어 있음
> `cpu0 6367 4 2360 4403129 9065 0 3972 0 0 0`\
> first `cpu`는 각 `cpuN`의 총합이고 그 외 나머지는 각각의 cpu 소요 시간에 대한 정보\
> 시간의 단위는 `USER_HZ` (보통은 hundredths of a second)\
> 각 열의 의미는 아래와 같다(행의 왼쪽부터 오른쪽)
> 
>>    * user: normal processes executing in user mode
>>    * nice: niced processes executing in user mode
>>    * system: processes executing in kernel mode
>>    * idle: twiddling thumbs
>>    * iowait: In a word, iowait stands for waiting for I/O to complete. But there are several problems:
>>        1. Cpu will not wait for I/O to complete, iowait is the time that a task is waiting for I/O to complete. When cpu goes into idle state for outstanding task io, another task will be scheduled on this CPU.
>>        1. In a multi-core CPU, the task waiting for I/O to complete is not running on any CPU, so the iowait of each CPU is difficult to calculate.
>>        1. The value of iowait field in /proc/stat will decrease in certain conditions. So, the iowait is not reliable by reading from /proc/stat.
>>  * irq: servicing interrupts
>>  * softirq: servicing softirqs
>>  * steal: involuntary wait
>>  * guest: running a normal guest
>>  * guest_nice: running a niced guest
* references : [Guide](https://github.com/Leo-G/Data-Science-Wiki), [Stack-over-flow](https://stackoverflow.com/questions/23367857/accurate-calculation-of-cpu-usage-given-in-percentage-in-linux)


## Process Data
* PID (Process Identifier)
* UID (User Identifier)
* Username
* Processor Utilization
* Memory Utilization
* Up Time

