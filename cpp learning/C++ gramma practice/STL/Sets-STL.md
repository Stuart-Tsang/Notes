# Sets-STL

1.利用erase函数 消除set中的元素

```cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <set>
#include <algorithm>
using namespace std;


int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */
    int query_num, type, tmp;
    set<int> s;

    cin >> query_num;
    for (int i = 0; i < query_num; ++i) {
        cin >> type >> tmp;
        if(type == 1){
            s.insert(tmp);
        }
        else if(type == 2){
            if(s.find(tmp) != s.end())
                s.erase(tmp);
        }
        else {
            if(s.find(tmp) != s.end())
                std::cout << "Yes" << std::endl;
            else
                std::cout << "No" << std::endl;
        }

    }
    return 0;
}




```

