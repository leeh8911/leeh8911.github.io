# 220616


* CMAKE
    * 현재 폴더를 기준으로 하위 폴더를 포함한 모든 파일의 경로를 참조
* 구글 엔지니어는 이렇게 일한다
    * 소프트웨어 엔지니어링이란
    * 팀워크 이끌어 내기
<!--more-->
# CMAKE
## 현재 폴더를 기준으로 하위 폴더를 포함한 모든 파일의 경로를 참조
```
FILE(GLOB_RECURSE SRC_FILES *.cpp)
```
* 현재 폴더를 기준으로 `*.cpp`의 패턴을 갖는 모든 파일의 경로를 `SRC_FILES`라는 이름으로 대체

# 구글 엔지니어는 이렇게 일한다
## 소프트웨어 엔지니어링이란
* 시간과 변경
* 규모 확장과 효율성
* 트레이드오프와 비용
* 소프트웨어 엔지니어링 vs 프로그래밍
## 팀워크 이끌어 내기
* 내 코드를 숨기고 싶어요
* 천재 신화
* 숨기는 건 해롭다
* 모든 건 팀에 달려 있다

