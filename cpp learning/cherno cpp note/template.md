# Template

优势：编译时自动生成重载函数，减少代码量。

劣势：发生错误时，要手动输入所有类型的参数，来找出产生错误的参数类型。

## 1.function template

对于不同参数类型，同一个函数要分别对其重载，代码量较大。

#### original source code

```cpp
#include <iostream>
#include <string>


void Print(int value){
    std::cout << value << std::endl;
}

void Print(std::string value){
    std::cout << value << std::endl;
}

void Print(float value){
    std::cout << value << std::endl;
}


int main()
{
    Print(5);
    Print("Hello!");
    Print(5.5f);
    
    std::cin.get();
}

```

引入模板，可以让编译器自己生成相应类型参数的重载函数，减少代码量

```cpp
template<typename T>
void Print(T value){
    std::cout << value << std::endl;
}
```

#### optimized source code

```cpp
#include <iostream>
#include <string>

template<typename T>
void Print(T value){
    std::cout << value << std::endl;
}

int main()
{
    Print(5);
    Print("Hello!");
    Print(5.5f);

    std::cin.get();
}

```

## 2. class template

```cpp
#include <iostream>
#include <string>

template<typename T, int N>
class Array{
private:
    T m_Array[N];
public:
    int GetSize() const {return N;}
};

int main()
{
    Array<std::string, 50> array;
    Array<int, 50> array;
    std::cout << array.GetSize() << std::endl;

    std::cin.get();
}

```

