计算机的文件存储在物理上都是二进制，文本文件和二进制之分，其实是一个人为的逻辑之分。

C读写文本文件与二进制文件的差别仅仅体现在回车换行符：

1. 写文本时，每遇到一个'\n'，会将其转换成'\r\n'\(回车换行\)。
2. 读文本时，每遇到一个'\r\n'，会将其转换成'\n'
3. 但是读写二进制文件的时候并不会做以上转换。

### 读写文本文件

#### fgets读取字符串

```
原型：char *fgets(char *buf, int bufsize, FILE *stream);

用法：#include <stdio.h>

功能：从stream中读取数据保存在buf指向的字符数组中，每次最多读取bufsize-1个字符（第bufsize个字符赋'\0'）

说明：如果文件中的该行，不足bufsize个字符，则读完该行就结束。如若该行（包括最后一个换行符）的字符数超过bufsize-1，
则fgets只返回一个不完整的行，但是，缓冲区总是以NULL字符结尾，对fgets的下一次调用会继续读该行。
```

#### fputs写入字符串

```
原型：int fputs(const char *str, FILE *stream)

用法：#include <stdio.h>

功能：向指定的文件写入一个字符串（不自动写入字符串结束标记符‘\0’）

说明：成功写入一个字符串后，文件的位置指针会自动后移，函数返回值为非负整数；否则返回EOF(符号常量，其值为-1)。
```

#### 例程

```
#include<stdio.h>
#include<stdlib.h>

void main(){

    //文件路径
    char* path = "D:\\test.txt";
    char* path_new = "D:\\test_new.txt";

    //打开文件，返回文件的指针
    FILE* f_read = fopen(path, "r");
    FILE* f_write = fopen(path_new, "w");

    //文件是否成功打开
    if (f_read == NULL || f_write == NULL){
        printf("文件打开失败");
        return;
    }

    //读取文件
    char buff[50];//缓冲区
    while (fgets(buff, 50, f_read)){
        //写文件
        fputs(buff, f_write);
    }

    //关闭文件
    fclose(f_read);
    fclose(f_write);

    system("pause");
}
```

### 读写二进制文件

#### fread读取二进制数据

```
原型：int fread ( void *buffer, int size, int count, FILE *stream) ;

用法：#include <stdio.h>

功能：从一个文件流中读数据，最多读取count个项，每个项size个字节

说明：如果调用成功返回实际读取到的项个数（小于或等于count），如果不成功或读到文件末尾返回 0。
```

#### fwrite写入二进制数据

```
原型：size_t fwrite(const void* buffer, size_t size, size_t count, FILE* stream);

用法：#include <stdio.h>

功能：向指定文件写入count个size字节的二进制数据

说明：成功写入一个字符串后，文件的位置指针会自动后移，函数返回值为非负整数；否则返回EOF(符号常量，其值为-1)。
```

### 例程

```
#include<stdio.h>
#include<stdlib.h>

void main(){

    //文件路径
    char* path = "D:\\test.png";
    char* path_new = "D:\\test_new.png";

    //打开文件，返回文件的指针，b代表是二进制文件
    FILE* f_read = fopen(path, "rb");
    FILE* f_write = fopen(path_new, "wb");

    //文件是否成功打开
    if (f_read == NULL || f_write == NULL){
        printf("文件打开失败");
        return;
    }

    //读取文件
    int buff[50];//缓冲区，注意，读写二进制文件的时候，是用int类型的缓冲区
    int len = 0; //每次读取到的长度
    //读到的内容放到缓冲区，缓冲区的单位大小，缓冲区大小（一个性读50个int的大小（4字节）的数据）
    //也就是一次读50 X 4 200字节的数据
    //返回的len是读取到的长度，小于等于50
    while ((len = fread(buff, sizeof(int), 50, f_read)) != 0){
        //写文件
        fwrite(buff, sizeof(int), len, f_write);
    }

    //关闭文件
    fclose(f_read);
    fclose(f_write);

    system("pause");
}
```

###### 注意：

1. 缓冲区用int类型的数组。
2. 文件读写模式后面加上b代表读写二进制文件。

### 获取文件大小

#### fseek设置文件指针stream的位置

```
原型：int fseek(FILE *stream, long offset, int fromwhere);

用法：#include <stdio.h>

功能：如果执行成功，stream将指向以fromwhere为基准，偏移offset（指针偏移量）个字节的位置，函数返回0。
如果执行失败(比如offset超过文件自身大小)，则不改变stream指向的位置，函数返回一个非0值。

说明：
```

```
#include<stdio.h>
#include<stdlib.h>

void main(){

    //文件路径
    char* path = "D:\\test.png";

    //打开文件，返回文件的指针，b代表是二进制文件
    FILE* f_read = fopen(path, "rb");

    //文件是否成功打开
    if (f_read == NULL){
        printf("文件打开失败");
        return;
    }

    //类似于多线程下载的概念，首先将文件长度按N段分，然后将每段文件读取并写入到相应的临时文件
    fseek(f_read, 0L, SEEK_END);//seek到文件的结尾，0L代表向前偏移几个字节
    long len = ftell(f_read);//返回当前的文件指针相对于文件开头的位移量
    printf("%ld", len);

    //关闭文件
    fclose(f_read);

    system("pause");
}
```



