### 开关文本文件

#### fopen打开文本

```
原型：FILE * fopen(const char * path, const char * mode);

用法：#include <stdio.h>

功能：打开文本

说明：一般而言，打开文件后会做一些文件读取或写入的动作，若打开文件失败，接下来的读写动作也无法顺利进行，
所以一般在 fopen() 后作错误判断及处理。

返回：文件顺利打开后，指向该流的文件指针就会被返回。如果文件打开失败则返回 NULL，并把错误代码存在errno中。
```

mode 有下列几种形态字符串：

| **字符串** | **说明** |
| :--- | :--- |
| r | 以只读方式打开文件，该文件必须存在。 |
| r+ | 以读/写方式打开文件，该文件必须存在。 |
| rb+ | 以读/写方式打开一个二进制文件，只允许读/写数据。 |
| rt+ | 以读/写方式打开一个文本文件，允许读和写。 |
| w | 打开只写文件，若文件存在则长度清为 0，即该文件内容消失，若不存在则创建该文件。 |
| w+ | 打开可读/写文件，若文件存在则文件长度清为零，即该文件内容会消失。若文件不存在则建立该文件。 |
| a | 以附加的方式打开只写文件。若文件不存在，则会建立该文件，如果文件存在，写入的数据会被加到文件尾，即文件原先的内容会被保留（[EOF](http://baike.baidu.com/item/EOF)符保留）。 |
| a+ | 以附加方式打开可读/写的文件。若文件不存在，则会建立该文件，如果文件存在，则写入的数据会被加到文件尾后，即文件原先的内容会被保留（原来的 EOF 符不保留）。 |
| wb | 以只写方式打开或新建一个二进制文件，只允许写数据。 |
| wb+ | 以读/写方式打开或建立一个二进制文件，允许读和写。 |
| wt+ | 以读/写方式打开或建立一个文本文件，允许读写。 |
| at+ | 以读/写方式打开一个文本文件，允许读或在文本末追加数据。 |
| ab+ | 以读/写方式打开一个二进制文件，允许读或在文件末追加数据。 |

####  fclose关闭文本文件

```
原型：int fclose( FILE *fp );

用法：#include <stdio.h>

功能：关闭文本文件

说明：使用fclose()函数就可以把缓冲区内最后剩余的数据输出到内核缓冲区，并释放文件指针和有关的缓冲区。

返回：如果流成功关闭，fclose 返回 0，否则返回EOF（-1）。
（如果流为NULL，而且程序可以继续执行，fclose设定error number给errno/EINVAL，并返回EOF。）
```





