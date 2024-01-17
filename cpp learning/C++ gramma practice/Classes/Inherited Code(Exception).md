# Inherited Code(Exception)



## 1.异常继承exception类

```cpp
class BadLengthException : exception {
private:
    string message_;
public:
    explicit BadLengthException(int length)
        : message_(to_string(length)){}

    // what()是exception类就有的？ 因此返回类型要一致？
    const char* what() const noexcept override {
        return message_.c_str();
    }
};
```

```cpp
#include <iostream>
#include <string>
#include <sstream>
#include <exception>
using namespace std;
class BadLengthException : exception {
private:
    string message_;
public:
    explicit BadLengthException(int length)
        : message_(to_string(length)){}

    const char* what() const noexcept override {
        return message_.c_str();
    }
};

bool checkUsername(string username) {
    bool isValid = true;
    int n = username.length();
    if(n < 5) {
        throw BadLengthException(n);
    }
    for(int i = 0; i < n-1; i++) {
        if(username[i] == 'w' && username[i+1] == 'w') {
            isValid = false;
        }
    }
    return isValid;
}

int main() {
    int T; cin >> T;
    while(T--) {
        string username;
        cin >> username;
        try {
            bool isValid = checkUsername(username);
            if(isValid) {
                cout << "Valid" << '\n';
            } else {
                cout << "Invalid" << '\n';
            }
        } catch (BadLengthException e) {
            cout << "Too short: " << e.what() << '\n';
        }
    }
    return 0;
}
```

