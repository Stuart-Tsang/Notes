# Rectangle Area

## 1. problem description

In this challenge, you are required to compute the area of a rectangle using classes.

Create two classes:

**Rectangle**

The *Rectangle* class should have two data fields-*width* and *height* of *int* types. The class should have *display()* method, to print the *width* and *height* of the rectangle separated by space.

**RectangleArea**

The *RectangleArea* class is derived from *Rectangle* class, i.e., it is the sub-class of *Rectangle* class. The class should have *read_input()* method, to read the values of *width* and *height* of the rectangle. The *RectangleArea* class should also overload the *display()* method to print the area of the rectangle.

**Input Format**

The first and only line of input contains two space separated integers denoting the width and height of the rectangle.

**Constraints**

- 

**Output Format**

The output should consist of exactly two lines:
In the first line, print the *width* and *height* of the rectangle separated by space.
In the second line, print the *area* of the rectangle.

**Sample Input**

```
10 5
```

**Sample Output**

```
10 5
50
```

**Explanation**

As, $width  = 10$ and $height = 5$, so $area = width * height = 50$.



## 2. solution

```cpp
#include <iostream>

using namespace std;
/*
 * Create classes Rectangle and RectangleArea
 */
class Rectangle{
protected:
    int width;
    int height;

public:
    void display(){
        std::cout << width << " " << height << std::endl;
    }
};

class RectangleArea : public Rectangle{
public:
    void read_input(){
        std::cin >> width >> height;
    }

    void display(){
        std::cout << width * height << std::endl;
    }
};


int main()
{
    /*
     * Declare a RectangleArea object
     */
    RectangleArea r_area;

    /*
     * Read the width and height
     */
    r_area.read_input();

    /*
     * Print the width and height
     */
    r_area.Rectangle::display();

    /*
     * Print the area
     */
    r_area.display();

    return 0;
}
```

