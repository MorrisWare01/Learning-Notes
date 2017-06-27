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

### 



