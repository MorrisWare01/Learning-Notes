### C语言中的内存模型

* 栈区：存放局部变量、自动分配和释放（自顶向下进栈出栈）
* 堆区：动态内存分配、最大值为操作系统的80%
* 全局区：静态区
* 常量区：存放字符串
* 程序代码区：存放代码

### 动态分配内存

#### malloc动态申请内存

```
原型：extern void *malloc(unsigned int size);

用法：#include <stdlib.h>

功能：向系统申请分配指定size个字节的内存空间

说明：void* 表示未确定类型的指针，void *可以指向任何类型的数据

返回：如果分配成功则返回指向被分配内存的指针(此存储区中的初始值不确定)，否则返回空指针NULL。

```

#### realloc动态内存调整

```
原型：extern void *realloc(void *mem_address, unsigned int newsize);

用法：#include <stdlib.h>

功能：动态内存调整

说明：先判断当前的指针是否有足够的连续空间，如果有，扩大mem_address指向的地址，并且将mem_address返回；如果空间不够，
先按照newsize指定的大小分配空间，将原有数据从头到尾拷贝到新分配的内存区域，而后释放原来mem_address所指内存区域
（注意：原来指针是自动释放，不需要使用free），同时返回新分配的内存区域的首地址。

返回：如果重新分配成功则返回指向被分配内存的指针，否则返回空指针NULL。
```

#### free释放内存

```
原型：void free(void *ptr)

用法：#include <stdlib.h>

功能：释放ptr指向的存储空间。

说明：被释放的空间通常被送入可用存储区池，以后可在调用malloc、realloc以及calloc函数来再分配。
```

动态申请内存

```
//堆内存分配,40M
int* p = (int*)malloc(1024*1024*10*sizeof(int));
if(p == NULL){
    printf("内存申请失败!");
}
```

初始化内存

```
//将p指向的空间清0
memset(p,0,sizeof(int));
```

重新分配内存

```
p=(int*)realloc(p,sizeof(int));
```

释放内存

```
//释放
if(p != NULL){
    free(p);
    p = NULL;
}
```



