# Vector-Erase

## 1.Erase

- *erase(int position):*

  ```
  Removes the element present at position.  
  Ex: v.erase(v.begin()+4); (erases the fifth element of the vector v)
  ```

- *erase(int start,int end):*

  ```
  Removes the elements in the range from start to end inclusive of the start and exclusive of the end.
  Ex:v.erase(v.begin()+2,v.begin()+5);(erases all the elements from the 
  ```



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
    int pos, head, tail;
    cin >> pos >> head >> tail;
    v.erase(v.begin()+ pos - 1);
    v.erase(v.begin() + head - 1 , v.begin() + tail - 1);

    cout << v.size() << endl;
    for (auto i: v) {
        cout << i << " ";
    }
    return 0;
}

```

