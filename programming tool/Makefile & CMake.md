

# Makefile and CMake

## 1. Makefile

### 必要性：

```sh
// 控制台每次这么写很繁琐，尤其是有很多个cpp文件的时候
g++ main.cpp factorial.cpp printhello.cpp -o main
```

Makefile脚本里面包含具体的编译细节，运行时只需要执行命令：

```sh
make
```

### Makefile文件编写

```makefile
## VERSION 1
hello: main.cpp printhello.cpp factorial.cpp
## tab
	g++ -o hello main.cpp printhello.cpp fatorial.cpp
	
## VERSION 2
## 对比VERSION 1会保留中间文件*.o
cxx = g++
TARGET = hello
OBJ = main.o printhello.o factorial.o

$(TARGET): $(obj)
	$(CXX) -o $(TARGET) $(OBJ)
	
main.o: main.cpp
	$(CXX) -c main.cpp

printhello.o: printhello.cpp
	$(CXX) -c printhello.cpp
	
factorial.o: factorial.cpp
	$(CXX) -c factorial.cpp
	
## VERSION 3
## 对比VERSION 2少写百分号前的文件和百分号后的文件
cxx = g++
TARGET = hello
OBJ = main.o printhello.o factorial.o

## -Wall means “warning all”
CXXFLAGS = -c -Wall

## '@'表示百分号前的变量，'^'表示百分号后的所有变量
## 为了少写一点
$(TARGET): $(OBJ)
	$(CXX) -o $@ $^
	
## '@'表示百分号前的变量，'<'表示百分号后的第一个变量
## 为了少写一点	 
%.o: %.cpp
	$(CXX) $(CXXFLAGS) $< -o $@

## clean 删除所有的.o文件和$(TARGET)文件
## 终端输入make clean执行clean对应的rm指令
## 伪命名：.PHONY是为了避免当前目录下本来有个clean文件 
## 猜测:make .PHONY可以执行删除指令吗？
.PHONY: clean
clean:
	rm -f *.o $(TARGET)
	
	
## VERSION 4
## 对比VERSION 3不用写对应的.cpp和.o文件
CXX = g++
TARGET = hello
SRC = $(wildcard *.cpp)
OBJ = $(patsubst %.cpp, %.o, $(SRC))

CXXFLAGS = -c -Wall

$(TARGET): $(OBJ)
	$(CXX) -o $@ $^

%.o: %.cpp
	$(CXX) $(CXXFLAGS) $< -o $@
	
.PHONY: clean
clean:
	rm -f *.o $(TARGET)
```



## 2. CMake

可以再不同的平台生成对应的Makefile

### 创建CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.10)

project(hello)

add_executable(hello main.cpp factorial.cpp printhello.cpp)
```

### 创建build文件夹

```shell
mkdir build && cd build
```

### cmake指令生成Makefile

会生成以下文件 

```
Makefile
CMakeCache.txt
CMakeFiles
cmake_install.cmake
```



```shell
# 根据上一级目录下的CMakeLists.txt生成Makefile
# cmake指令生成的文件都在build目录中，方便管理(clean)
cmake ..
```

### make执行Makefile文件

```sh
make
```

