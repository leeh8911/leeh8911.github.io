# 220607


* 메모리 주소와 16진수
* CppND-System-Monitor-Project (Review)
<!--more-->
# Udacity
## 메모리 주소와 16진수
* John Atanasoff가 두개의 숫자로 이루어진 부호화 시스템을 제안('부재'를 나타내는 숫자와 '존재'를 나타내는 두개의 숫자)
* 2진수 대신에 16진수를 사용하는 이유
    * 가독성: 16진수가 2진수에 비해 10진법 표현에 가까워 가독성이 높음
    * 정보 밀도: 0~255의 수를 표현하고자 할 때 16진수는 2개의 숫자만 있으면 되지만, 2진수는 8개가 필요함
    * `byte`로의 변환: 모든 컴퓨터는 byte로 표현된 주소를 사용하고 8개의 비트로 표현됨.(byte는 8bit)
* GDB (GNU DeBugger)

## CppND-System-Monitor-Project (Review)
* 반복적인 코드를 최소화 하기 위해선 몇몇 일반적인 함수들을 정의해야 함
* [C++ Reference Material Style Convections](https://cs.stmarys.ca/~porter/csc/ref/cpp_style.html)
* [Why we must close every opened file in C++](https://www.quora.com/Why-we-must-close-every-opened-file-in-C++) : 파일을 닫지 않아도 크게 문제될 것은 없지만 권장되지 않는 사항임
* VmSize: Virtual memory size, VmRSS: exact physical memory
* [Stackoverflow - Global variable "count" ambiguous](https://stackoverflow.com/questions/11271889/global-variable-count-ambiguous)
* 적절한 생성자가 있다면 벡터에 원소를 추가할 때 명시적으로 하지 않아도 됨
```cpp
// 적절한 생성자
Process::Process (int pid) { _pid = pid; ...} 

// 다른 어딘가
vector<Process> processes_ = {};
for (const int &pid : pids) {
    processes_.emplace_back(pid); 
    // processes_.emplace_back(Process(pid)); // 컴파일러가 알아서 적당한 생성자를 찾아줌(없으면 안되고..)
}
```
* [chrono librarry tutorial](https://www.youtube.com/watch?v=P32hvk8b13M)
* Make file과 연관된 몇몇 링크들
    * [GNU MakeFile Documentation](https://www.gnu.org/software/make/manual/html_node/Standard-Targets.html#Standard-Targets)
    * [A Simple Makefile Tutorial](https://cs.colby.edu/maxwell/courses/tutorials/maketutor/)
    * [Variable Name Convention](https://makefiletutorial.com/)
* 몇몇 하드 코딩된 변수들은 LinuxParser.h로 옮기는 것을 추천


