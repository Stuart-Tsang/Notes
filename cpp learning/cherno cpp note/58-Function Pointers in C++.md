# 58-Function Pointers in C++



## Generalize: assign a function to a variable

## assign function pointer(weird code)

```cpp
#include <iostream>
#include <vector>

void HelloWorld(int value){
    std::cout << "Hello World! Value: "<< value << std::endl;
}


int main() {

    void(*HelloWorldFunction)(int);
    HelloWorldFunction = HelloWorld;

    HelloWorldFunction(8);

    return 0;
}
```



## typedef assign function pointer

```cpp
#include <iostream>
#include <vector>

void HelloWorld(int value){
    std::cout << "Hello World! Value: "<< value << std::endl;
}


int main() {

    typedef void(*HelloWorldFunction)(int);
    HelloWorldFunction func = HelloWorld;

    func(8);

    return 0;
}
```

## function pointer as function parameters

```cpp
#include <iostream>
#include <vector>

void PrintValue(int& value){
    std::cout << value << std::endl;
}

void ForEach(const std::vector<int>& values, void(*func)(int&)){
    for(int value : values){
        func(value);
    }
}

int main() {

    std::vector<int> MyList = {1,2,3,4,5};
    ForEach(MyList, PrintValue);
    
    return 0;
}

```



## function pointer as function para (lambda version)

```cpp
#include <iostream>
#include <vector>

void ForEach(const std::vector<int>& values, void(*func)(int&)){
    for(int value : values){
        func(value);
    }
}

int main() {

    std::vector<int> MyList = {1,2,3,4,5};
    ForEach(MyList, [](int& tmp){ std::cout << "Value:" << tmp << std::endl; });

    return 0;
}

```

