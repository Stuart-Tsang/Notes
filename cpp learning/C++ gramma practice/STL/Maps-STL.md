# Maps-STL

## 源码

```cpp
#include <cmath>
#include <cstdio>
#include <map>
#include <iostream>
#include <algorithm>
using namespace std;




int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */
    int query_num, type, tmp;
    string name;
    std::map<string, int> m;

    cin >> query_num;
    for (int i = 0; i < query_num; ++i) {
        cin >> type >> name;
        if(type == 1){
            cin >> tmp;
            if(m.find(name) != m.end())
                m[name] += tmp;
            else
                m.insert(make_pair(name, tmp));
        }
        else if(type == 2){
            if(m.find(name) != m.end())
                m.erase(name);
        }
        else {
            if(m.find(name) != m.end())
                std::cout << m[name] << std::endl;
            else
                std::cout << "0" << std::endl;
        }

    }
    return 0;
}


```

