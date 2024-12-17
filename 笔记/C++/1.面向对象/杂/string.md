### string::npos

**“pos!= string::npos”** 在 C++ 中通常用于判断一个子字符串在给定字符串中是否被找到。其中 “pos” 通常是一个整数类型的变量，表示子字符串在给定字符串中的位置。如果 “pos” 的值不等于 “string::npos”，就说明子字符串在给定字符串中被找到了，因为 “string::npos” 是一个特殊的值，表示没有找到子字符串。例如，如果我们使用字符串查找函数在一个字符串中查找某个子字符串，如果返回的位置不等于 “**string::npos**”，就可以确定子字符串存在于该字符串中。

### isdigit(str[0]) 用于判断是否位数字

### statement.find_first_not_of(" ")

~~~cpp
value.erase(0, value.find_first_not_of(" "));
~~~

### string var = statement.substr(0, pos)

~~~cpp
#include <iostream>
#include <sstream>
#include <string>
using namespace std;

int main() {
    string input;
    getline(cin, input);
    int a = 0, b = 0, c = 0;
    stringstream ss(input);
    string statement;
    while (getline(ss, statement, ';')) {
        statement.erase(0, statement.find_first_not_of(" "));
        statement.erase(statement.find_last_not_of(" ") + 1);
        size_t pos = statement.find(":=");
        if (pos != string::npos) {
            string var = statement.substr(0, pos);
            string value = statement.substr(pos + 2);
            value.erase(0, value.find_first_not_of(" "));
            value.erase(value.find_last_not_of(" ") + 1);
            if (value.size() == 1 && isdigit(value[0])) {
                int val = value[0] - '0';
                if (var == "a") {
                    a = val;
                } else if (var == "b") {
                    b = val;
                } else if (var == "c") {
                    c = val;
                }
            } else {
                if (var == "a") {
                    if (value == "b") {
                        a = b;
                    } else if (value == "c") {
                        a = c;
                    }
                } else if (var == "b") {
                    if (value == "a") {
                        b = a;
                    } else if (value == "c") {
                        b = c;
                    }
                } else if (var == "c") {
                    if (value == "a") {
                        c = a;
                    } else if (value == "b") {
                        c = b;
                    }
                }
            }
        }
    }
    cout << a << " " << b << " " << c << endl;
    return 0;
}
~~~

