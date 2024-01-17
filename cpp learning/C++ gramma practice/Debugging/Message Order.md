# Message Order

## 1.	问题描述

信息的传输过程可能会乱序(代码利用random_shuffle函数实现)，即接收方接收的包的排序跟发送方的发送顺序不一样。

**Sample Input 0**

```
Alex
Hello Monique!
What'up?
Not much :(
```

**Sample Output 0**

```
Alex
Hello Monique!
What'up?
Not much :(
```

## 2.	实现

### 2.1	结构

+ 体会这几个类的整体设计和互相作用
+ sort函数会调用代排序的实例类型的重载函数
+ 注意getline函数什么时候会return false(文件结尾，不能通过输入什么字符串，只能ctrl+Z或是代码逻辑中对结尾有条件判断)



```c++
class Message {
private:
    // 利用static关键字统计发送的包的总数量，给每个Messsage实例一个数值唯一的变量rank,来标志Message的发送顺序
    static int count;
    // 变量rank标志Message的发送顺序
    int rank;
    // 变量message表示发送的信息
    string message;
    
public:
    Message() {
        // 随着Message数量增加，静态统计变量要+1
        rank = count++;
    }
    Message(const string& text) : message(text) {
        rank = count++;
    }

    const string& get_text() {
        return message;
    }
	// 重载"<",Recipient类的sort函数执行时会调用该重载函数
    bool operator<(const Message& msg){
        return this->rank < msg.rank;
    }
};
```

```C++
class MessageFactory {
public:
    MessageFactory() {}
    Message create_message(const string& text) {
        return Message(text);
    }
};
```

```c++
class Recipient {
public:
    Recipient() {}
    void receive(const Message& msg) {
        messages_.push_back(msg);
    }
    void print_messages() {
        fix_order();
        for (auto& msg : messages_) {
            cout << msg.get_text() << endl;
        }
        messages_.clear();
    }
private:
    void fix_order() {
        // 会调用Message类的重载函数<
        sort(messages_.begin(), messages_.end());
    }
    vector<Message> messages_;
};
```

```C++
class Network {
public:
    static void send_messages(vector<Message> messages, Recipient& recipient) {
        // simulates the unpredictable network, where sent messages might arrive in unspecified order
        random_shuffle(messages.begin(), messages.end());
        for (auto msg : messages) {
            recipient.receive(msg);
        }
    }
};
```



## Src

```C++
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

class Message {
private:
    static int count;
    int rank;
    string message;
public:
    Message() {
        rank = count++;
    }
    Message(const string& text) : message(text) {
        rank = count++;
    }

    const string& get_text() {
        return message;
    }

    bool operator<(const Message& msg){
        return this->rank < msg.rank;
    }
};

class MessageFactory {
public:
    MessageFactory() {}
    Message create_message(const string& text) {
        return Message(text);
    }
};

class Recipient {
public:
    Recipient() {}
    void receive(const Message& msg) {
        messages_.push_back(msg);
    }
    void print_messages() {
        fix_order();
        for (auto& msg : messages_) {
            cout << msg.get_text() << endl;
        }
        messages_.clear();
    }
private:
    void fix_order() {
        sort(messages_.begin(), messages_.end());
    }
    vector<Message> messages_;
};

class Network {
public:
    static void send_messages(vector<Message> messages, Recipient& recipient) {
        // simulates the unpredictable network, where sent messages might arrive in unspecified order
        random_shuffle(messages.begin(), messages.end());
        for (auto msg : messages) {
            recipient.receive(msg);
        }
    }
};

int Message::count = 0;

int main() {
    MessageFactory message_factory;
    Recipient recipient;
    vector<Message> messages;
    string text;
   while (getline(cin, text)) {
        messages.push_back(message_factory.create_message(text));
    }
    Network::send_messages(messages, recipient);
    recipient.print_messages();
}

```

