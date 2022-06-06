# 220606


Git
* Git commit 날짜 바꾸기
Udacity
* ElapsedTime (seconds data convert HH:MM:SS)
* sysconf
* istringstream.good
* Memory Management Overview
<!--more-->
# Git
## Git commit 날짜 바꾸기
* `git commit --amend --no-edit --date "DD MM YYYY hh:mm:ss"`
* 특정 커밋에 대해 `--amend`는 이전 커밋 내용에 덮어쓰기의 의미
* `--no-edit`은 현재 커밋 내용을 수정사항 없이 반영하겠다는 의미
* `--date`는 날짜에 대한 옵션

# Udacity
## ElapsedTime (seconds data convert HH:MM:SS)
* `<iomanip>`헤더 파일의 `std::setfill('0')`를 이용해 공백 자리를 `0`으로 채워넣고, `std::setw(2)`로 폭을 2로 설정해 놓음
* `<sstream>` 헤더 파일의 `std::stringstream`을 이용해 문자열의 처리를 `<<` 연산으로 해결
```cpp
#include <sstream>
#include <iomanip>
#include <string>

std::string foo(int32_t seconds){
  int32_t second = seconds % 60;
  seconds /= 60;
  int32_t minute = seconds % 60;
  int32_t hour = seconds / 60;

  stringstream ss("");
  ss << std::setfill('0') << std::setw(2) <<
  hour << ":" << minute << ":" << second;

  return ss.str();
}

```

## sysconf
* `sysconf` 런타임에 대한 설정 정보 획득
* [reference](https://man7.org/linux/man-pages/man3/sysconf.3.html)
* `sysconf(_SC_CLK_TCK)` : 초당 클락(clock) 틱 수 정보를 얻음

## istringstream.good
* `good` 스트림의 상태가 좋은지 확인
* [std::ios::good](https://m.cplusplus.com/reference/ios/ios/good/)

## Memory Management Overview
1. Overview of Memory Types
2. Variables and Memory
3. Dynamic Memory Allocation
4. Resource Copying Policies
5. Smart Pointers
6. Project: Memory Management Chatbot


