# Pointer

## 1.用abs()求绝对值(absoluted difference)

```cpp
#include <stdio.h>
#include <cstdlib>	//abs所属头文件，<cmath>头文件重载了浮点类型
void update(int *a,int *b) {
    // Complete this function
    int temp1 = *a + *b;
    int temp2 = std::abs(*a - *b);
    *a = temp1;
    *b = temp2;
}

int main() {
    int a, b;
    int *pa = &a, *pb = &b;

    scanf("%d %d", &a, &b);
    update(pa, pb);
    printf("%d\n%d", a, b);

    return 0;
}
```

## 2.abs源码实现

```cpp

```

