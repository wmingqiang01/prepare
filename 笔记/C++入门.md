# C++入门

### 第一个c++程序：hello world

```c++
#include <iostream>
using namespace std;

int main() {
    std::cout << "Hello, World!" << std::endl;

    return 0;
}

```

`#include <iostream>`是头文件，`iosteam`是C++中用于输入输出的头文件。

`usnamespace std`是引用C++标准库，在标准库中，使用std中的函数，在前面加`std::`加入引用这句以后可以不需要再加这个前缀。但是要防止命名冲突。

`cout`是C++中用于输出的对象，类似与c中的`printf`。所有标准数据类型均可以使用`cout`输出。`cin`是用于输出的对象。箭头>>表示的是数据的流向。在例程中，字符串流向`cout`，因此箭头指向`cout`，输入格式为`cin>>name`，表示数据由输入流向变量.`name`.`cin.getline（cSring, 1000）`用于读取整行，但是需要注明字符数的上限。注意：`cin`的速度比`scanf`慢很多，建议用`scanf`.

输出小数用`printf`更加方便，C++格式的输出需要用到`<inmanip>`头文件，用`cout.setprecistion(int digit)`修正精度。

`endl`等于`\n`，有些细节的不同。

### 基础数据类型

```c++
int numbei = 1;
char character = 'a';
bool boolean = true;
char* cString = 'Hello World';
string cppString = 'World'; //在使用string时，需要引用string库
```

### cin判断EOF

```
int n,m;
while(cin>>n>>m){

}
```

### C++语法特性

1. bool类型
2. 动态开辟内存：在C++中，用`new`动态开辟内存，同c中的`malloc`，C++中不支持变长数组
3. 引用：用&创建引用，引用可以看作不可以改变对象的指针。在函数传参时才会用到，简化指针的代码
4. 函数重载：函数是以函数名与参数列表来区分的。两个函数名可以相同，但是参数列表返回值不同。函数的部分参数可以缺省，以缺省值代替。
5. stuck：结构在c++中直接使用和结构名，不需要使用`typedef`。在struct中可以加入与结构同名，无返回值的构造函数。在创建stuct的时候会自动调用构造函数

# C++标准库   使用`include <bits/stdc++.h>`包含所有头文件

## vector `include <vector>`

 vector可以看作一个超级数组，可以向数组一样用下标访问，也可以像链表动态改变长度。

```c++
vector<int> arr1(100);//尖括号用于声明元素数据类型，圆括号声明响亮的大小
int arr2[100];//数组

vector<int> list;//将向量看作一个链表，动态变长
list.push_back(1);//在数组尾部插入数值1
list.push_back(2);
list.push_back(3);
```

#### `iterator`迭代器与普通指针的使用方法对比

```c++
vector<int> arr1(100);//尖括号用于声明元素数据类型，圆括号声明响亮的大小
int arr2[100];//数组

vector<int>::iterator p1;
int* p2;
//迭代器
for(p1 = arr1.begin();p1!=arr1.end();p1++){
    cout<<*p1<<endl;
}
//普通指针
for(p2=arr2, int i = 0;i<n;i++,p2++){
    cout<<*p2<<endl;
}
```

#### `vector`的基本操作

```c++
list.clear();//清空O(1)
list.size();//数组大小O(n)
list.empty();//数组是否为空O(1)
list.begin();//数组首元素迭代器O(1)
list.end();//数组最后一个元素的下一个元素迭代器，在数组中实际不存在O(1)
list.erase(怕);//删除数组某个迭代器所在位置的元素O(n)
list.push_back(1);//在数组末尾添加一个元素O(1)
list.pop_back();//删除数组最后乙骨元素O(1)
```

## `<string>`字符串

`string`字符串在C++中可以看作一个`char`元素组成的``vector`.

```c++
//string的基本操作
string str = 'hello';
str.length();str.size();//str的大小
str.insert(position，strings);//在位置position处插入字符串strings，position可以是下表是或迭代器
str.c_str();//将str转换为C中的字符串，用于printf输出
str.append(str2);//将str2接到str1的末尾
str.compare(str2);//stcmp(str, str2)
str == str2;//stcmp(str, str2) == 0
str += str2;//str.append(str2)
str +='a'//str.push_back('a')
```

## algorithm算法函数`include <algorithm>`

####  1.快速排序

```c++
vector<int> arr
//sort(start, end, mathod)start为开始指针，end为结束指针，(最有一个元素的后一个元素的指针),method表示排序依据，默认是升序

sort(arr.begin(), arr.end());
for(vector<int>::iteraor it=arr.begin;it!=arr.end();it++){
    printf('%d\n',*it);
}

bool cmp(int a,int b){
    return a>b;
}
sort(arr.begin(),arr.end(),cmp);
```

#### 2.其他算法函数

```c++
//最大最小值
min(1,2);max(1,2);
//数组最大最小值所在指针
min_element(arr.begin(),arr.end());
max_element(arr.begin(),arr.end());
//数组中第n小的元素放到第n个位置（从0开始，方法类似快排）
nth_element(arr.begin(),arr.bengin()+n,arr.end());
//交换两个数的位置
swap(arr[0],arr[1]);
//翻转数组
reverse(arr.begin(),arr.end());
//去除重复元素,要求arr是有序数组
unique(arr.bengin(),arr.end());
//二分查找
bool isExit = binary_search(arr.bengin(),arr.end(),1);
// 如果将一个元素插入数组应该插进那个位置
//lowe_bound返回第一个插入位置的指针，upper_bound返回最后一个位置的指针
int first_loc = lowe_bound(arr.begin(),arr.end(),2);
int last_loc = upper_bound(arr.begin(),arr.end(),2);
```

