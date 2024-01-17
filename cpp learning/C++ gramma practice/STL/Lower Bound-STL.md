# Lower Bound-STL

## 1.lower_bound()函数

```cpp
lower_bound (ForwardIterator first, ForwardIterator last, const T& val);
/*
Returns an iterator pointing to the first element in the range [first,last) which does not compare less than val.
*/
/*
可以利用该函数检验某个元素val是否在vector中，若函数返回的iter相应的值value跟调用函数时的val不同，则vector不存在元素val;
若相同，则vector中存在元素val。
*/

// lower_bound/upper_bound example
#include <iostream>     // std::cout
#include <algorithm>    // std::lower_bound, std::upper_bound, std::sort
#include <vector>       // std::vector

//lower_bound example
int main () {
  int myints[] = {10,20,30,30,20,10,10,20};
  std::vector<int> v(myints,myints+8);           // 10 20 30 30 20 10 10 20

  std::sort (v.begin(), v.end());                // 10 10 10 20 20 20 30 30

  std::vector<int>::iterator low,up;
  low=std::lower_bound (v.begin(), v.end(), 20); //          ^
  up= std::upper_bound (v.begin(), v.end(), 20); //                   ^

  std::cout << "lower_bound at position " << (low- v.begin()) << '\n';
  std::cout << "upper_bound at position " << (up - v.begin()) << '\n';

  return 0;
}
```

## 2.源码

```cpp
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
    vector<int>::iterator it,low;
    int query_num;
    cin >> query_num;
    for (int i = 0; i < query_num; ++i) {
        cin >> tmp;
        
		/*
		可以利用该lower_bound()函数检验某个元素val是否在vector中，		若函数返回的iter相应的值value跟调用函数时的val不同，则			vector不存在元素val;若相同，则vector中存在元素val。
		故可以不用find()函数
		*/
        // it = std::find(v.begin(), v.end(), tmp);
        low = lower_bound(v.begin(), v.end(), tmp);
        
        if (*low == tmp){
            cout << "Yes " << (it - v.begin() + 1) << endl;
        }
        else {
            cout << "No " << (low - v.begin() + 1) << endl;
        }
    }

    return 0;
}

```

