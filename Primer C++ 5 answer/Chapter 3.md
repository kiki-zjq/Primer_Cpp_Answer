# Chapter 3. 标准库类型string #

###3.2###
读入一整行
```
int main() {
	string a ;
	while (getline(cin,a)) {
		cout << a << endl;
	}
	
	return 0;

}
```

一次读入一个单词
```
int main() {
	string a ;
	while (cin>>a) {
		cout << a << endl;
	}
	
	return 0;

}
```

---

###3.3###

+ 对于string类的输入函数，它会自动忽略开头的空白（空格、制表符、换行等等），从第一个真正的字符开始直到下一个空白。
+ 对于getline()函数，它会保存字符串中的空白符，它读入数据，直到遇到换行符位置。

---

###3.4###

比较字符串大小
```
int main() {
	string a , b;
    cin >> a >> b;
	if (a != b)
	{
		cout<<(a >= b ? a : b)<<endl;
	}

	
	return 0;

}
```

比较字符串长度
```
int main() {
	string a , b;
    cin >> a >> b;
	if (a.size() != b.size())
	{
		cout<<(a.size() >= b.size() ? a : b)<<endl;
	}
	else
	{
		cout<<"The length of these strings are the same!"<<endl;
	}

	
	return 0;

}
```

---

###3.5###

```
int main(){
    string mystring;
	string sumstring;
	while (getline(cin ,mystring))
	{
		sumstring += mystring;
        //sumstring = sumstring+mystring+" ";
		cout<<sumstring<<endl;
	}
    return 0;
}

```

---

###3.6###

```
int main(){
    string mystring = "test";


    for(auto &c:mystring){
        c='X';
    }
    cout << mystring << endl;
    return 0;
}

```

---

###3.7###

这里只用char的话也是可以的，因为每一个元素都是char类型的。

---

###3.8###

for比较简单，while的话还需要知道string的长度<br/>
另外比较重要的一点是size()函数只读取到string的第一个空格为止

---

###3.9###

不合法，因为字符串S是一个空字符串，第一个元素是未知的，引用非法

---

###3.10###

```
int main() {
	string mystring;
	cin >> mystring;
	for (auto &c : mystring) {
		if (!ispunct(c))
			cout << c;
	};
	return 0;
}
```

---

###3.11###

只看for()括号内的是合法的<br/>
但是如果{}花括号内有一些赋值操作之类的，就是不合法的

---

###3.12###

- a. 正确，创建了一个元素为vector的vector对象
- b. 不正确，类型不一致
- c. 正确，创建了10个null对象

---

###3.13###

- 0
- 10个0
- 10个42
- 1个10
- 2个，10和42
- 1个10
- 10个"hi"

---

###3.14###

```
#include <iostream>
#include <string>
#include <vector>
using std::string;
using std::cin;
using std::cout;
using std::endl;

int main() {
	std::vector<int> myVect;
	int i;
	while (cin >> i) {
		myVect.push_back(i);
	};
	return 0;
}
```

---

###3.15###

```
int main() {
	std::vector<string> myVect;
	string i;
	while (cin >> i) {
		myVect.push_back(i);
	};
	return 0;
}
```

---

###3.16###

```
int main() {
	std::vector<int> myVect;
	int i;
	while (cin >> i) {
		myVect.push_back(i);
	};
	for (auto c : myVect){
		cout << c ;
	}
	return 0;
}
```

---

###3.17###

```

int main()
{
	std::vector<string> My_vector;
	string istring;
	while (cin >> istring)
	{
		My_vector.push_back(istring);
	}
	for (int i = 0; i < My_vector.size(); i++)
		for (int j = 0; j < My_vector[i].length(); j++)
		{
			My_vector[i][j] = toupper(My_vector[i][j]);
		}
	for (int i = 0; i < My_vector.size(); i++)
	{
		cout << My_vector[i] << endl;
	}
	return 0;
}

```

---

###3.18###

不合法，不能用下标添加元素，用push_back()

---

###3.19###

```

vector<int> ivec2{ 42, 42, 42, 42, 42, 42, 42, 42, 42, 42};
vector<int> My_int2(10,42);
vector<int> My_int3 = My_int2;

```

---

###3.20###

```

int main()
{
	std::vector<int> My_vector;
	int i;
	while (cin >> i)
	{
		My_vector.push_back(i);
	}

	for (int i = 0; i < My_vector.size() - 1; ++i) {
		cout << My_vector[i] + My_vector[i + 1]<<" ";
	}
	return 0;
}

```

改动后

```

int main()
{
	std::vector<int> My_vector;
	int i;
	while (cin >> i)
	{
		My_vector.push_back(i);
	}
	int size = My_vector.size();
	for (int i = 0; i < size/2; ++i) {
		cout << My_vector[i] + My_vector[size - i -1]<<" ";
	}
	return 0;
}


```

---

###3.21###

---

###3.22###

```


#include <iostream>
#include <string>
#include <vector>
using namespace std;
void main()
{	
	vector<int> text(10);
	for (int i = 0; i < 10;i++)
	{
		cin>>text[i];
	}
	for (auto vector_begin = text.begin(), vector_end = text.end();vector_begin != vector_end;vector_begin++) 
	{
		vector_end--;
		cout<<*vector_begin + *vector_end<<endl;	
	}
}

```

---

###3.23###

```


#include <iostream>
#include <string>
#include <vector>
using namespace std;
void main()
{	
	vector<int> text(10,5);
	for (auto it = text.begin(); it != text.end();it++) //注意判断其是否为空
	{
		*it = *it * 2;
		cout<<*it<<endl;	
	}
}

```

---

###3.27###

- a.非法，buf_size不是常量
- b.合法
- c.非法，函数返回值不是常量
- d.非法，需要留一个空间放空字符

---

###3.28###

- sa[10],sa2[10] 10个空对象
- ia[10],ia2[10] 10个0

---

###3.29###

长度不可扩展，一旦定义，不能再更改长度。

---

###3.30###

```

constexpr size_t array_size = 10;
int ia[array_size]; // 下标越界，最大为9.
for (size_t ix = 1; ix <= array_size; ix ++) { // 下标范围为0--9，而不是1--10
    ia[ix] = ix;
}

```

---

###3.31###

```
#include <iostream>
#include <string>
#include <vector>
using std::string;
using std::cin;
using std::cout;
using std::endl;

int main()
{
	int a[10];

	for (int i = 0; i < 10; i++) {
		a[i] = i;
	}

	for (auto j : a) {
		cout << j << "--";
	}
	cout << endl;
	return 0;
}


```

---

###3.32###

```

int main(){
      {
      vector<int> vec(10);

      for (int i = 0; i < 10; i++) {
          vec[i] = i;
      }   

      for (auto iter : vec) {
          cout << iter << "---";
      }   
      cout << endl;

      vector<int> vec1(vec);
      for (auto iter1 : vec1) {
          cout << iter1 << "...";
      }   
      cout << endl;
    }
    return 0;
}

```

---

###3.33###

不初始化scores，则其中内容未知，可能为空，也可能有别的数据

---

###3.34###

p1 += p2 - p1; p2-p1为p1与p2之间的距离，p1+（p1和p2之间的距离），即最后得到p2的值。当p1或p2不在同一数组内，则程序非法。

```

int main()
  {
      int a[10] = {1, 3, 0, 9, 7, 5, 4, 11, 12, 15};

      int *p1 = a; //*p1 = 1;
      int *p2 = &a[5]; // *p2 = 5

      p1 += p2 - p1; 

      cout << "p1 = " << *p1 << endl; // *p1 = 5;

      return 0;
  }

```

---

###3.35###

```
int main()
  {
      int a[10] = {1, 3, 0, 9, 7, 5, 4, 11, 12, 15};

      int *p1 = a; //*p1 = 1;

      for (int i = 0; i < 10; i++) {
          p1[i] = 0;
      }   

      for (auto j : a) {
          cout << j << "---";
      }

   return 0; 
  }
```

---

###3.36###
