# Basic Datatype

## 1.利用fixed和setprecision限制浮点数的精度

```C++
#include <iostream>
#include <cstdio>
#include <iomanip>
using namespace std;

int main() {
    // Complete the code.
    int a;
    long long int b;
    char c;
    float d;
    double e;
    cout << sizeof(long);
    cin >> a >> b >> c >> d >> e;
    cout << a << endl;
    cout << b << endl;
    cout << c << endl;
    // without 'fixed' ,results become '334' and '14049.3049'
    // specify the right part of the dot with 'fixed'
    cout << fixed << setprecision(3) << d << endl;
    cout << fixed << setprecision(9) << e << endl;
    return 0;
}

```

