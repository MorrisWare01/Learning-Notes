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



