### 获取文件大小

#### fseek设置文件指针stream的位置

```
原型：int fseek(FILE *stream, long offset, int fromwhere);

用法：#include <stdio.h>

功能：如果执行成功，stream将指向以fromwhere为基准，偏移offset（指针偏移量）个字节的位置，函数返回0。
如果执行失败(比如offset超过文件自身大小)，则不改变stream指向的位置，函数返回一个非0值。

说明：fromwhere：（偏移起始位置：文件头0(SEEK_SET)，当前位置1(SEEK_CUR)，文件尾2(SEEK_END)）
```

#### ftell得到文件位置指针当前位置相对于文件首的偏移字节数

```
原型：long ftell(FILE *stream);

用法：#include <stdio.h>

功能：用于得到文件位置指针当前位置相对于文件首的偏移字节数。

说明：使用fseek函数后再调用函数ftell()就能非常容易地确定文件的当前位置。

注意：因为ftell返回long型，根据long型的取值范围-231~231-1（-2147483648～2147483647），故对大于2.1G的文件进行操作时出错。
```

#### 例程

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



