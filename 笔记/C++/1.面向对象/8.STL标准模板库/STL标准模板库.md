**标准模板库**（`Standard Template Library`）中包含了很多实用的组件，利用这些组件，程序员编程方便而高效。

### 1 Vector

vector容器与数组类似，包含一组地址连续的存储单元。对vector容器可以进行很多操作，包括查询、插入、删除等常见操作。

~~~cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
	vector<int> nums;
	nums.insert(nums.begin(), 99);
	nums.insert(nums.begin(), 34);
	nums.insert(nums.end(), 1000);
	nums.push_back(669);

	cout << "\n当前nums中元素为: " << endl;
	for (int i = 0; i < nums.size(); i++)
		cout << nums[i] << " " ;

	cout << nums.at(2);
	nums.erase(nums.begin());
	nums.pop_back();

	cout << "\n当前nums中元素为: " << endl;
	for (int i = 0; i < nums.size(); i++)
		cout << nums[i] << " " ;

	return 0;
}
~~~

### 2 list容器

~~~cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
	list<int> number;
	list<int>::iterator niter;
	number.push_back(123);
	number.push_back(234);
	number.push_back(345);

	cout << "链表内容：" << endl;
	for (niter = number.begin(); niter != number.end(); ++niter)
		cout << *niter << endl;
	number.reverse();
	cout << "逆转后的链表内容：" << endl;
	for (niter = number.begin(); niter != number.end(); ++niter)
		cout << *niter << endl;
	number.reverse();

	return 0;
}
~~~

### 3 stack

**例子：**利用栈进行进制转换

~~~cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
	stack<int> st;
	int num = 100;
	cout << "100的八进制表示为：";
	while (num) {
		st.push(num % 8);
		num /= 8;
	}
	int t;
	while (!st.empty()) {
		t = st.top();
		cout << t;
		st.pop();
	}
	cout << endl;

	return 0;
}
~~~

### 4 queue

~~~cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
	queue<int> qu;
	for (int i = 0; i < 10; i++) 
		qu.push(i * 3 + i);
	while (!qu.empty()) {
		cout << qu.front() << " ";
		qu.pop();
	}
	cout << endl;

	return 0;
}
~~~

### 5 优先队列priority_queue

~~~cpp
#include <iostream>
#include <queue>
#include <functional>
#include <cstdlib>
#include <ctime>
using namespace std;

int main() {
	priority_queue<int> pq;
	srand((unsigned)time(0));
	for (int i = 0; i < 6; i++) {
		int t = rand();
		cout << t << endl;
		pq.push(t);
	}
	cout << "优先队列的值：" << endl;
	for (int i = 0; i < 6; i++) {
		cout << pq.top() << endl;
		pq.pop();
	}

	return 0;
}
~~~

### 6 双端队列deque

~~~cpp
push_back();
push_front();
insert();
pop_back();
pop_front();
erase();
begin();
end();
rbegin();
rend();
size();
maxsize();
~~~

### 7 set

~~~cpp
#include <iostream>
#include <set>
#include <string>
using namespace std;

int main() {
	set<string> s;
	s.insert("aaa");
	s.insert("bbb");
	s.insert("ccc");
	if (s.count("aaa") != 0) {
		cout << "存在元素aaa" << endl;
	}
	set<string>::iterator iter;
	for (iter = s.begin(); iter != s.end(); ++iter) 
		cout << *iter << endl;

	return 0;
}
~~~

### 8 map

~~~cpp
#include <iostream>
#include <map>
#include <string>
using namespace std;

int main() {
	map<string, int> m;
	m["aaa"] = 111;
	m["bbb"] = 222;
	m["ccc"] = 333;
	if (m.count("aaa")) {
		cout << "键aaa对应的值为" << m.at("aaa") << endl;
		cout << "键aaa对应的值为" << m["aaa"] << endl;
	}

	return 0;
}
~~~

