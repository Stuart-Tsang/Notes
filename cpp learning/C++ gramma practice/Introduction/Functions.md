# Functions

## 1.问题：函数比较参数大小包含过多分支,而且代码冗余

```
#include <iostream>
#include <cstdio>
using namespace std;

/*
Add `int max_of_four(int a, int b, int c, int d)` here.
*/
int max_of_four(int a, int b, int c, int d){
    if(a > b && c > d){
        if(a > c) return a;
        else return c;
    }
    else if(a > b && c < d){
        if(a > d) return a;
        else return d;
    }
    else if(a < b && c > d){
        if(b > c) return b;
        else return c;
    }
    else{
        if(b > d) return b;
        else return d;
    }

}

int main() {
    int a, b, c, d;
    scanf("%d %d %d %d", &a, &b, &c, &d);
    int ans = max_of_four(a, b, c, d);
    printf("%d", ans);

    return 0;
}
```

## 2.设置一个哨兵max值减少分支，避免代码冗余

```cpp
#include <iostream>
#include <cstdio>
using namespace std;

/*
Add `int max_of_four(int a, int b, int c, int d)` here.
*/
int max_of_four(int a, int b, int c, int d){
    int max = a;
    if(max < b) max = b;
    if(max < c) max = c;
    if(max < d) max = d;
    return max;
}

int main() {
    int a, b, c, d;
    scanf("%d %d %d %d", &a, &b, &c, &d);
    int ans = max_of_four(a, b, c, d);
    printf("%d", ans);

    return 0;
}
```

