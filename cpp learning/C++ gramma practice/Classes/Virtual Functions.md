# Virtual Functions

## 1.	类中的静态(static keyword)变量(所有实例共享)

​		**Note: 值的初始化不是在定义处，也不在函数体内**

```cpp
class Professor : public Person{
private:
	...
public:
    static int number;
}

int Professor::number = 0;

int main(){
    
}
```



## Complete Source Code

```cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

class Person{
public:
    string name;
    int age;
public:
    Person() = default;
    Person(const string& name_, const int& age_)
        : name(name_), age(age_){}

    virtual void getdata() = 0;
    virtual void putdata() = 0;
};

class Student : public Person{
private:
    // marks, which is an array of size 6 and cur_id
    int cur_id;
    int marks[6];
    // vector<int> marks
public:
    static int number;

    void getdata() override {
        string name_;
        int age_;
        // input the name, age and the marks of the student in 6 subjects.
        cin >> name_ >> age_;
        this->name = name_;
        this->age = age_;
        this->cur_id = ++number;

        int count = 0;
        while(count < 6){
            cin >> this->marks[count];
            count++;
        }


    }
    void putdata() override {
        // print the space separated name, age, the sum of the marks in 6 subjects and id on a new line
        int sum = 0;
        for (int i = 0; i < 6; ++i) {
            sum+= marks[i];
        }
        cout << this->name << " " << this->age << " " << sum << " " << this->cur_id << endl;
    }
};

class Professor : public Person{
private:
    // publications and cur_id
    int publications;
    int cur_id;
public:
    static int number;
    Professor() = default;
    /*
     * Professor(const string& name_, const int& age_, const int& publications_, const int& cur_id_)
        : Person(name_,age_), publications(publications_), cur_id(cur_id_){}
    */
    void getdata() override {
        string name_;
        int age_, publications_;
        // input the name, age and publications of the professor
        cin >> name_ >> age_ >> publications_;
        this->name = name_;
        this->age = age_;
        this->publications = publications_;
        this->cur_id = ++number;
    }
    void putdata() override {
        // print the space separated name, age, publications and id on a new line
        cout << this->name << " " << this->age << " " << this->publications << " " << this->cur_id << endl;
    }
};

int Student::number = 0;
int Professor::number = 0;
int main(){

    int n, val;
    cin>>n; //The number of objects that is going to be created.
    Person *per[n];

    for(int i = 0;i < n;i++){

        cin>>val;
        if(val == 1){
            // If val is 1 current object is of type Professor
            per[i] = new Professor;

        }
        else per[i] = new Student; // Else the current object is of type Student

        per[i]->getdata(); // Get the data from the user.

    }

    for(int i=0;i<n;i++)
        per[i]->putdata(); // Print the required output for each object.

    return 0;

}

```

