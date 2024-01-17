# C++ Class Template

## Example & Note

```c++
template <class T>
class MyTemplate {
T element;
public:
MyTemplate (T arg) {element=arg;}
T divideBy2 () {return element/2;}
};
```



```c++
// class template specialization:
template <>
class MyTemplate <char> {
char element;
public:
MyTemplate (char arg) {element=arg;}
char printElement ()
{
return element;
}
};
```

### string.append()和“+”的速度差异

从结果来看，“+”更快