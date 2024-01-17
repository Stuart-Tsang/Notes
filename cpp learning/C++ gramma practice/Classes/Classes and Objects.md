# Classes and Objects

## 1. 可以用vector替代数组，并用accumulate()来求和(C++20)

```cpp
// Write your Student class here
class Student {
private:
    int scores[5];
public:
    void input(){
        for (int i = 0; i < 5; i++) {
            cin >> scores[i];
        }
    }

    int calculateTotalScore() {
        int sum = 0;
        for (int i = 0; i < 5; i++) {
            sum += scores[i];
        }
        return sum;
    }
};
```



