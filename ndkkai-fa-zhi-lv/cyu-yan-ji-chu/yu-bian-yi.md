### 预编译（预处理include、define）

#### C语言的执行流程

1. 编译：形成目标代码\(.obj\)。
2. 连接：将目标代码与C函数库连接合并，形成最终的可执行文件。
3. 执行。

预编译（预处理），为编译做准备工作，完成代码文本的替换工作。

头文件告诉编译器有这样一个函数，连接器负责找到这个函数的实现，通过include引入。实现的话，在哪里都可以。类似于Android布局文件中的include标签。

例子

创建text.txt文件：

```
printf("我被包含进来了");
```

在主函数里面使用：

```
#include<stdio.h>
#include<stdlib.h>

void main(){

    #include "text.txt"

    system("pause");
}
实质上会把include标签替换成我们自己的text.txt文件里面的内容。
```

实质上会把include标签替换成我们自己的text.txt文件里面的内容。

#### 宏定义、宏替换



