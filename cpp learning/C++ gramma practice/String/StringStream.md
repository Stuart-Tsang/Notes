# StringStream



## 1.处理输入字符串的逗号

**Sample Input**

```
23,4,56
```

**Sample Output**

```
23
4
56
```

```cpp
#include <sstream>
#include <vector>
#include <iostream>
using namespace std;

vector<int> parseInts(string str) {
    // Complete this function
    stringstream ss(str);
    // Here is a storage area for the discarded commas.
    char ch;
    int a;
    vector<int> tmp;
    while(ss){
        ss >> a >> ch;
        tmp.push_back(a);
    }
    return tmp;
}

int main() {
    string str;
    cin >> str;
    vector<int> integers = parseInts(str);
    for(int i = 0; i < integers.size(); i++) {
        cout << integers[i] << "\n";
    }

    return 0;
}
```

