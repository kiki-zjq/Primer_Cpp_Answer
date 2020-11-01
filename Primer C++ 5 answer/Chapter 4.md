# Chapter 4. 基础 #

###4.1###

105

---

###4.2###

- *vec.begin() ==> *(vec.begin())
- vec.begin() + 1 ==> (vec.begin() + 1)

---

###4.4###
```
int result = 12 / 3 * 4 + 5 * 15 +24 % 4 / 2;
cout << result << endl;
```

---

###4.5###
- -86
- -18
- 0
- -2

---

###4.6###
```
int num;
cin >> num;
num % 2 == 1 ? cout << "odd" << endl : cout << "even" << endl;
```

---

###4.7###
溢出，当计算结果超出该类型所能表示的范围就会产生溢出<br/>
short c = (short)65538;

---

###4.8###
相等运算符先求值，逻辑与、逻辑或运算优先级相同，按照从左到右的顺序求值

---

###4.9###
cp是一个地址，不为0。再取*cp的值，为一个字符串，不为0.最后两者相与，值为真

---

###4.10###
```
int num;
while(cin>>num && num!=42){...}
```

---

###4.11###

```
if ((a>b) && (b>c) && (c>d))
```

---

###4.12###
先取i值，再计算j < k是否成立，成立为大于0的数，否则为0。再计算i != (j < k)

---

###4.13###
- i = 3, d = 3;
- d = 3.5, i = 3;

---

###4.14###

- 报错，不可以给常量42赋值
- 给i赋值为42，if判断结果为真

---

###4.15###

主要是给pi赋值非法（也不算非法，就是意义不明显），因为pi存的是地址。应该改成*pi = 0

---

###4.16###
- if ((p = getPtr) != 0)
- if(i==1024)

---

###4.18###

会先向后移动一个元素，再输出移动后的值。输出范围为第二个元素到最后一个元素的下一个元素。由于最后一个元素的下一个元素未知，所以会访问到未知内存

---

###4.19###

```
ptr != 0 && *ptr++;        //判断ptr是否为空，并且ptr指向的值是否为0；
ival ++ && ival;                // 判断ival及ival++是否为空。运算的顺序为，先计算++，在进行&&
vec[ival++] <= vec[ival];    // 运算顺序未知，比如ival = 1，编译器有可能先算vec[ival++]，得到ival=2，再计算vec[ival]，这样就得不到预期结果。因此改成vec[ival+1] <= vec[ival];
```

---

###4.20###

```
*iter++;                    // 合法，先对iter+1，再返回iter初始值的副本，再对该副本进行解引用
(*iter)++;                  //  不合法，不能对string类型进行++操作。
*iter.empty();           // 不合法，不能对指针指向的值判空。可改为(*iter).empty();
iter->empty();          // 合法
++*iter;                    // 不合法，先求*iter，在进行++操作，不能对string类型做++操作，可改为 *（++iter）；
iter++->empty();      //合法，++和->的优先级一样，所以遵循自左向右结合，先算iter++的值，返回iter初始值的副本，再进行empty()判断。iter->empty等价于(*iter).empty
```

---

###4.21###

```
void test421()
  {
      vector<int> ivec = {1, 2, 3, 4, 5, 6}; 

      for (auto &iter : ivec) {
          iter = (iter % 2 == 1) ? iter * 2 : iter;
          cout << iter << " ";
      }   
      cout << endl;
}
```

---

###4.22###

```
void test422()
  {   
      int grade;
      string finalgrade;

      while (cin >> grade)
      {
      // approach 1
          finalgrade = (grade > 90) ? "high pass" : ((grade < 60) ? "fail" : ((grade < 75) ? "low pass" : "pass"));

      // approch 2    
          if (grade > 90)
          {   
              finalgrade = "hign pass";
          }
          else if (grade < 60)
          {   
              finalgrade = "fail";
          }
          else if (grade < 75)
          {   
              finalgrade = "low pass";
          }
          else
          {   
              finalgrade = "pass";
          }

          cout << finalgrade << endl;
      }
  }
```

---

###4.23###

```
string s = "word";
//    string p1 = s + s[s.size()-1] == 's' ? "" : "s";
 //  条件语句优先级较低，要给其加括号。
   string p1 = s + (s[s.size()-1] == 's' ? "" : "s");
```

---

###4.25###

'q' << 6运算会把结果隐式转化为int类型，因为6是int类型。因此结果的二进制码为：<br/>
0000 0000 0000 0000 0001 1100 0100 0000，转化为10进制为7232.

---

###4.26###

在某些系统上，int占16为，因此如果用unsigned int来存储的话，在这些机器上就会发生位数不够用的情况。而unsigned long则可以保证在任何机器上都至少有32位。

---

###4.27###

```
unsigned long ul1 = 3, ul2 = 7;
cout << (ul1 & ul2) << endl;            // 0011 & 0111 = 0011 = 3
cout << (ul1 | ul2) << endl;              // 0011 | 0111 = 0111 = 7
cout << (ul1 && ul2) << endl;          // 3 && 7 = 1
cout << (ul1 || ul2) << endl;4.28     // 3 || 7 = 1
```

---

###4.28###

```
void test428()
  {   
      cout << sizeof (int) << endl;                // 4
      cout << sizeof (char) << endl;             // 1
      cout << sizeof (short) << endl;            // 2
      cout << sizeof (long) << endl;             // 8
      cout << sizeof (float) << endl;              // 4
      cout << sizeof (double) << endl;          // 8
      cout << sizeof (long double) << endl;  // 16
      cout << sizeof (long long) << endl;      // 8
  }
```

---

###4.29###

```
void test429()
  {
      int x[10];
      int *p = x;

      cout << sizeof(x)/sizeof(*x) << endl;         // 10, sizeof(x) = 10*4, sizeof(*x) = 4;
      cout << sizeof(p) / sizeof (*p) << endl;     // 2, sizeof(p)的含义：p是一个int *类型，因此得出的大小应该是指针的大小。
                                                                      // sizeof(*p)的含义：*p已经对p解引用了，*p实际就是int类型，因此sizeof(*p)得到的是一个int型的大小。
  }
```

---

###4.30###

```
sizeof x +  y;                // sizeof(x) +  y; 
sizeof p->mem[i];        // sizeof (p->mem[i]); 
sizeof a < b;                // sizeof (a) < b;   
sizeof f();                     // sizeof (f()); 
```

---

###4.31###