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

