# Conditional Statements

## 1.太多分支费时间(比如属于最后一个else if 的情况要判断前面所有的分支条件)

```c++
#include <bits/stdc++.h>

using namespace std;

string ltrim(const string &);
string rtrim(const string &);



int main()
{
    string n_temp;
    getline(cin, n_temp);

    int n = stoi(ltrim(rtrim(n_temp)));

    // Write your code here
    if(n == 1){
        cout << "one";
    }
    else if(n == 2){
        cout << "two";
    }
    else if(n == 3){
        cout << "three";
    }
    else if(n == 4){
        cout << "four";
    }
    else if(n == 5){
        cout << "five";
    }
    else if(n == 6){
        cout << "six";
    }
    else if(n == 7){
        cout << "seven";
    }
    else if(n == 8){
        cout << "eight";
    }
    else if(n == 9){
        cout << "nine";
    }
    else {
        cout << "Greater than 9";
    }

    return 0;
}

string ltrim(const string &str) {
    string s(str);

    s.erase(
            s.begin(),
            find_if(s.begin(), s.end(), not1(ptr_fun<int, int>(isspace)))
    );

    return s;
}

string rtrim(const string &str) {
    string s(str);

    s.erase(
            find_if(s.rbegin(), s.rend(), not1(ptr_fun<int, int>(isspace))).base(),
            s.end()
    );

    return s;
}

```



## 2.利用数组将对应的英文字符串存储起来避免了多个else if分支

```C++
#include <bits/stdc++.h>

using namespace std;

string ltrim(const string &);
string rtrim(const string &);



int main()
{
    string n_temp;
    getline(cin, n_temp);

    int n = stoi(ltrim(rtrim(n_temp)));

    string num[] = {"one","two","three","four","five","six","seven","eight","nine"};

    // Write your code here
    if(n >= 1 && n <= 9){
        cout << num[n-1];
    }
    else {
        cout << "Greater than 9";
    }

    return 0;
}

string ltrim(const string &str) {
    string s(str);

    s.erase(
            s.begin(),
            find_if(s.begin(), s.end(), not1(ptr_fun<int, int>(isspace)))
    );

    return s;
}

string rtrim(const string &str) {
    string s(str);

    s.erase(
            find_if(s.rbegin(), s.rend(), not1(ptr_fun<int, int>(isspace))).base(),
            s.end()
    );

    return s;
}

```

## 3.stoi(string to integer)

```cpp
int n = stoi(ltrim(rtrim(n_temp)));
```

