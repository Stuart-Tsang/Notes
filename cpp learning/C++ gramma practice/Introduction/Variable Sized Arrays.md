# Variable Sized Arrays

## 1.二维vector构造，改变数组长度用resize()

```cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;


int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */
    int lines_len, query_num;
    cin >> lines_len >> query_num;
    // 2D array(empty now)
    vector<vector<int>> bigarray;
    int length;
    for(int i = 0; i < lines_len; i++){
        cin >> length;
        //vector<int> array(n);
        //empty now
        vector<int> array;
        for (int j = 0; j < length; ++j) {
            int temp;
            cin >> temp;
            array.push_back(temp);
        }
        
         //Pushing back above 1D vector
        // to create the 2D vector
        bigarray.push_back(array);	
    }

    for (int i = 0; i < query_num; ++i) {
        int x,y;
        cin >> x >> y;
        cout << bigarray[x][y] << endl;
    }
    return 0;
}

```

