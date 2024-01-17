# Strings

## 1.把string当作字符数组访问/修改单个字母

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    // Complete the program
    string a,b;
    cin >> a >> b;
    cout << a.size() << " " << b.size() << endl;
    cout << a + b << endl;
    string tmp(a);
    a[0] = b[0];
    b[0] = tmp[0];
    cout << a << " " << b << endl;
    return 0;
}
```

