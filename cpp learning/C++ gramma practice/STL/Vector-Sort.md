# Vector-Sort

## 1.分类函数 sort(v.begin() , v.end()

```
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;


int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */
    int length,tmp;
    vector<int> v;
    cin >> length;
    for (int i = 0; i < length; ++i) {
       cin >> tmp;
        v.push_back(tmp);
    }
    sort(v.begin(),v.end());
    for (auto i: v) {
        cout << i << " ";
    }
    return 0;
}

```

