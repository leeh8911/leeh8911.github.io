# 220608


* Type of Computer Memory
* Cache Memory
* Virtual Memory
<!--more-->
# Udacity
## Type of Computer Memory
* Computer Memory Latency and Size Hierarchy
    * CPU
    * Cache L1, L2
    * RAM Physical RAM, Virtual Memory
    * Permanent Storage Areas Removable Drives, Hard Dist, Network

## Cache Memory
* Cache memory는 매우 빠르지만, 용량이 엄청 작음 (일반적인 RAM에 비해)
* RAM에 있는 정보를 바로 CPU로 이동시켜 연산하기엔 오버헤드가 크기 때문에 Cache를 활용함
* Cache를 잘 활용하기
```cpp
#include <chrono>
#include <iostream>

int main()
{
    // create array 
    const int size = 4;
    static int x[size][size];

    auto t1 = std::chrono::high_resolution_clock::now();
    for (int i = 0; i < size; i++)
    {
        for (int j = 0; j < size; j++)
        {
            x[j][i] = i + j; // 이중 배열 x에 접근하기 위한 접근자가 i가 바깥 for-loop, j가 안쪽 for-loop
            				 // x[j][i]에서 i 주변의 메모리를 캐싱하겠지만, 실제 반복되는 for-loop는 j
            				 // 이기 때문에 두개의 순서를 바꿔줌으로서 캐싱을 활용한 수행속도를 빠르게 할 								 //수 있다.
            std::cout << &x[j][i] << ": i=" << i << ", j=" << j << std::endl;
        }
    }

    // print execution time to console
    auto t2 = std::chrono::high_resolution_clock::now(); // stop time measurement
    auto duration = std::chrono::duration_cast<std::chrono::microseconds>(t2 - t1).count();
    std::cout << "Execution time: " << duration << " microseconds" << std::endl;

    return 0;
}
```

## Virtual Memory
* Several memory-related problems:
	* Holes in address space
	* Programs writing over each other
* 메모리 관련 문제 해결에 가상 메모리가 큰 도움
* 32-bit 시스템은 32-bit의 주소 공간을 갖고 있음 -> 사용 가능 최대 메모리 공간 $2^{32}$-bit = 4 GB




