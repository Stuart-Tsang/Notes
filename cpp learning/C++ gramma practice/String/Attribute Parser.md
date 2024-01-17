# Attribute Parser



## 1.  利用栈来实现从属关系

**Sample Input**

```cpp
4 3
<tag1 value = "HelloWorld">
<tag2 name = "Name1">
</tag2>
</tag1>
tag1.tag2~name
tag1~name
tag1~value
```



```cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
#include <sstream>
#include <unordered_map>
using namespace std;


int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */
    int N,Q;
    cin >> N >> Q;

    string line, tmp;
    string prefix, key, value;
    getline(cin, line);

    vector<string> prefix_stack;
    unordered_map<string, string> attr;
    for (int i = 0; i < N; ++i) {

        getline(cin, line);

        // remove symbol "<" and ">"
        line.erase(line.end()-1);
        line.erase(line.begin(),line.begin()+1);

        if(line[0] == '/'){
            // line.erase(line.begin(), line.begin()+1);
            prefix_stack.pop_back();
            continue;
        }

        // replace symbol "\" and "=" with " "
        replace(line.begin(), line.end(), '\"', ' ');
        replace(line.begin(), line.end(),'=',' ');

        stringstream ss(line);

        ss >> prefix;


        prefix_stack.push_back(prefix);

        string tmp_prefix = prefix_stack[0];
        for (int j = 1; j < prefix_stack.size(); ++j) {
            tmp_prefix += '.' + prefix_stack[j];
        }
        while(ss){
            ss >> key >> value;
            attr[tmp_prefix + '~' + key] = value;
        }

    }

    string query;
    for (int i = 0; i < Q; ++i) {
        cin >> query;
        // getline(cin, query);
        if(attr.find(query) == attr.end()){
            cout << "Not Found!" << endl;
        }
        else
            cout << attr[query] << endl;
    }
    return 0;
}

```

