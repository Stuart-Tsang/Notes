# Array Introduction

```cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;


int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */
    int length = 0;
    scanf("%d", &length);
    int arr[length];
    for(int i = 0; i < length; i++){
        cin >> arr[i];
    }
    for(int i = length-1; i >=0; i--){
        if(i != length-1)
            cout << " ";
        cout << arr[i];
    }
    return 0;
}

```

