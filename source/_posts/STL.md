---
title: STL天下第一！！！
date: 2023-5-1
tags: STL
---



<!-- more -->
**STL天下第一！！！！！**   

------------   
### 与STL有关及STL中包含的数据结构都会写在此篇   

### **vector(不定长数组)**  
需调用``<vector>``头文件   
函数   
1. **size/empty**   
size函数返回vector长度，empty返回一个bool类型，表示是否为空，时间复杂度皆为O（1）。      

~~其实所有STL容器都支持此操作~~   

2. **clear**   
清空数组  
3. **迭代器**  
可以看为STL容器的指针，可以用*解除引用。   
一个保存``int``的``vector``的迭代器的声明方式为：  
``vector<int>::iterator it``
it便为迭代器，可以与其它整数相加减

4. **begin/end** （左开右闭）   
begin返回第一个元素，end返回最后一个元素的后一位（front和back等效）   
5. **push_back()和pop_back()**   
push将元素插入尾部，pop将元素从头部移除   




### **queue队列**  
头文件为``<queue>``   
1. 循环队列``queue``   
``push``  
``pop``   
``front``   
``back``   
(大同小异所以不再详解)   
2. 优先队列``priority_queue``
``push`  
``pop``   
``top`` (查询堆顶元素/默认为最大值)   
### 细谈优先队列   

优先队列有三个参数，分别是要储存的数据类型，所使用容器（默认为``vector``），优先级判定（默认大根堆）。


优先队列的优先级也是可以和``sort``一样改变的！

只要在结构体中重载<运算符即可。
~~~c++
queue<int> q;
struct rec{…}; queue<rec> q;                        //结构体rec中必须定义小于号
priority_queue<int> q;                              // 大根堆
priority_queue<int, vector<int>, greater<int>> q;   // 小根堆，greater是已编写好的。
priority_queue<pair<int, int>>q;
~~~


 ### **栈stack**  

 头文件为``<stack>``   
 ``push``   
 ``pop``

 无话可说  
 ###  **双端队列deque**   

 头文件与queue相同 

 []              // 随机访问   
``begin/end``       // 返回deque的头/尾迭代器  
``front/back``      // 队头/队尾元素   
``push_back``       // 从队尾入队   
``push_front``      // 从队头入队   
``pop_back``        // 从队尾出队   
``pop_front``       // 从队头出队   
``clea``r           // 清空队列  

### **集合set**   

头文件为``<set>``

#### ``set``

声明

  ``set<int> s;``   
``struct rec{…}; set<rec> s;``  // 结构体rec中必须定义小于号   
``multiset<double> s;``

1. ``size/empty/clear``    
与vector类似，不在讲
2. ``insert``   
``insert(x)``将x插入到set中
3.  ``begin/end``
返回集合的首、尾迭代器，时间复杂度均为 O(1)O(1)。  
``s.begin()``是指向集合中最小元素的迭代器。   
``s.end()``是指向集合中最大元素的下一个位置的迭代器。换言之，就像``vector``一样，是一个“前闭后开”的形式。因此-- ``s.end()``是指向集合中最大元素的迭代器。
4. ``find``
``s.find(x)``在集合s中查找等于x的元素，并返回指向该元素的迭代器。若不存在，则返回``s.end()``。时间复杂度为 O(logn)  
5. count
s.count(x)返回集合s中等于x的元素个数，时间复杂度为 O(k+logn)O(k+logn)，其中 kk 为元素x的个数。

### **map**  

头文件为``<map>``

map容器是一个键值对key-value的映射，其内部实现是一棵以key为关键码的红黑树。Map的key和value可以是任意类型，其中key必须定义小于号运算符。

``map<key_type, value_type> name;``

1.  ``size/empty/clear/begin/end``
均与set类似。

2.  ``insert/erase``
与set类似，但其参数均是pair<key_type, value_type>。

3.  ``find``
h.find(x)在变量名为h的map中查找key为x的二元组。

4.  ``[]``操作符
h[key]返回key映射的value的引用，时间复杂度为 O(logn)O(logn)。

[]操作符是map最吸引人的地方。我们可以很方便地通过h[key]来得到key对应的value，还可以对h[key]进行赋值操作，改变key对应的value。



 






