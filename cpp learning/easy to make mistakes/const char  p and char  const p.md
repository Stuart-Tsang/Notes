# const char * p and char * const p

## 1. const char * p

similar to char const *p

const 修饰 *p ：p指向的内存单元所存储的值不能改变

### sample

```cpp
#include <iostream>

int main() {
    char a = 'a';
    char b = 'a';
    char c = 'a';
    
    const char *p =&a;
    char const *q = &b;
    p = &b;
    q = &a;
    *p = 'b';// error: read-only
    *q = 'c';// error: read-only	

    // char* const o = &b;
    // o = &c;
    // *o = 'b';
    return 0;
}

```

### error message

```
Read-only variable is not assignable :12
Read-only variable is not assignable :13
```

## 2. char * const p

const 修饰指针 ：不能指向另一个存储单元

### sample

```cpp
#include <iostream>

int main() {
    char a = 'a';
    char b = 'a';
    char c = 'a';

    // const char *p =&a;
    // char const *q = &b;
    // p = &b;
    // q = &a;
    // *p = 'b';
    // *q = 'c';

    char* const o = &b;
    o = &c;// error
    *o = 'b';
    return 0;
}

```

### error message

```
cannot assign to variable 'o' with const-qualified type 'char *const' :16
```

