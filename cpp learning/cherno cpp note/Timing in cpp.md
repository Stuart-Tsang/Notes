# Timing in C++

## library chrono

```cpp
#include <iostream>
#include <chrono>
#include <thread>

int main()
{
    using namespace std::literals::chrono_literals;

    auto start = std::chrono::high_resolution_clock::now();
    std::this_thread::sleep_for(1s);
    auto end = std::chrono::high_resolution_clock::now();

    std::chrono::duration<float> duration = end - start;
    std::cout << duration.count() << "s " << std::endl;

    std::cin.get();
}

```



## 2.	Timer Struct

```cpp
#include <iostream>
#include <chrono>


struct Timer{
    std::chrono::high_resolution_clock::time_point start, end;
    std::chrono::duration<float> duration;

    Timer(){
        start = std::chrono::high_resolution_clock::now();
    }

    ~Timer(){
        end = std::chrono::high_resolution_clock::now();
        duration = end - start;

        float ms = duration.count() * 1000.0f;
        std::cout << "Timer took " << ms << "ms" << std::endl;
    }
};

void Function()
{
    Timer timer;

    for (int i = 0; i < 100; i++){
        std::cout << "Hello" << std::endl;
    }
}

int main()
{
    Function();

    std::cin.get();
}

```

##  



