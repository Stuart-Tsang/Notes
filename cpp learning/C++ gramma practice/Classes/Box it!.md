# Box it!

## 1.	3个int类型相乘溢出，位数不够，先转换再相乘

```cpp

#include<bits/stdc++.h>

using namespace std;
//Implement the class Box
//l,b,h are integers representing the dimensions of the box
class Box{
private:
    int l = 0,b = 0,h = 0;

public:
// The class should have the following functions :

// Constructors:
// Box();
// Box(int,int,int);
// Box(Box);
    Box(){
        l = 0;
        b = 0;
        h = 0;
    }

    Box(int _l, int _b, int _h){
        l = _l;
        b = _b;
        h = _h;
    }

    Box(const Box&) = default;  //?

// int getLength(); // Return box's length
    int& getLength() {
        return l;
    }
// int getBreadth (); // Return box's breadth
    int& getBreadth() {
        return b;
    }
// int getHeight ();  //Return box's height
    int&  getHeight() {
        return h;
    }
// long long CalculateVolume(); // Return the volume of the box
    long long  CalculateVolume() {
        long long tmp = (long long)l * (long long)b * (long long)h;
        int tmp1 = l * b * h;
        long long tmp2 = l * b * h;
        long long tmp3 = (long long)tmp1;
        return (long long)l * (long long)b * (long long)h;
    }

//Overload operator < as specified
//bool operator<(Box& b)
    bool operator<(Box& other){
        if(this->l < other.l)
            return true;
        if(this->b < other.b && this->l == other.l)
            return true;
        if(this->h < other.h && this->b == other.b && this->l == other.l)
            return true;
        return false;
    }


//Overload operator << as specified
//ostream& operator<<(ostream& out, Box& B)
    friend ostream& operator<<(ostream& out, Box& B){
        return out << B.l <<" "<< B.b << ' '<< B.h;
    }

};


void check2()
{
    int n;
    cin>>n;
    Box temp;
    for(int i=0;i<n;i++)
    {
        int type;
        cin>>type;
        if(type ==1)
        {
            cout<<temp<<endl;
        }
        if(type == 2)
        {
            int l,b,h;
            cin>>l>>b>>h;
            Box NewBox(l,b,h);
            temp=NewBox;
            cout<<temp<<endl;
        }
        if(type==3)
        {
            int l,b,h;
            cin>>l>>b>>h;
            Box NewBox(l,b,h);
            if(NewBox<temp)
            {
                cout<<"Lesser\n";
            }
            else
            {
                cout<<"Greater\n";
            }
        }
        if(type==4)
        {
            cout<<temp.CalculateVolume()<<endl;
        }
        if(type==5)
        {
            Box NewBox(temp);
            cout<<NewBox<<endl;
        }

    }
}

int main()
{
    check2();
}
```

