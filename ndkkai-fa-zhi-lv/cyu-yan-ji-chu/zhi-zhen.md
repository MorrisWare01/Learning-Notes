### 指针

指针是一个变量，也叫指针变量，存放的是变量的地址（内存地址，系统给数据分配的编号（门牌号）），有类型之分。

### 指针的意义

没有指针就没有Java的面向对象（OOP）。

### NULL指针

NULL 指针是一个定义在标准库中的值为零的常量。

在变量声明的时候，如果没有确切的地址可以赋值，为指针变量赋一个 NULL 值是一个良好的编程习惯。

### 函数指针

* 函数指针常量：void fun\(int x\);
* 函数指针变量：void \(\*fun\)\(int \);
* 函数指针作为参数（类似java回调函数）

```
#include <stdio.h>

int add(int a,int b){
    return a + b;
}

int minus(int a,int b){
    return a - b;
}

void operate(int (*fun)(int,int),int a,int b){
    printf("%d",fun(a,b));
}

int main(){
    operate(add,1,1);
    operate(minus,2,1);

}
```







