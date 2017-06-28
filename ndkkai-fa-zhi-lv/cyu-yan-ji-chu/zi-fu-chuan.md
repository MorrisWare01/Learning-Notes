### 创建

字符数组实现。数组可以修改其中某一个值，不可以整体赋值。

字符指针实现。字符指针不可以修改其中某一个值，可以整体赋值。使用指针加法，结合结束符，可以进行截取。

### 字符串常用的方法（\#include &lt;string.h&gt;）

#### strcpy字符串赋值

```
原型：extern char *stpcpy(char *dest,char *src);

用法：#include <string.h>

功能：把src所指由NULL结束的字符串复制到dest所指的数组中。

说明：src和dest所指内存区域不可以重叠且dest必须有足够的空间来容纳src的字符串。

返回：指向dest的指针。

注意：因为底层需要进行单个字符的操作，因此dest需要是一个字符数组类型，且空间必须足够大。
```

#### strcat字符串拼接

```
原型：extern char *strcat(char *dest,char *src);

用法：#include <string.h>

功能：把src所指字符串添加到dest结尾处(覆盖dest结尾处的'\0')并添加'\0'。

说明：src和dest所指内存区域不可以重叠且dest必须有足够的空间来容纳src的字符串。

返回：指向dest的指针。
```

#### strlen字符串长度

```
原型：extern unsigned int strlen(char *s);

用法：#include <string.h>

功能：计算给定字符串的（unsigned int型）长度，不包括'\0'在内

说明：返回s的长度，不包括结束符NULL。
```

#### strcmp字符串比较

```
原型：extern int strcmp(const char *s1,const char *s2);

用法：#include <string.h>

功能：如果s1和s2是相同的，则返回0；如果s1<s2则返回小于0；如果s1>s2则返回大于0。
```

#### strchr字符查找

```
原型：extern char *strchr(char *s,char c);

用法：#include <string.h>

功能：查找字符串s中首次出现字符c的位置

说明：返回首次出现c的位置的指针，如果s中不存在c则返回NULL。
```

#### strstr字符串查找

```
原型：extern char *strstr(char *haystack, char *needle);

用法：#include <string.h>

功能：从字符串haystack中寻找needle第一次出现的位置（不比较结束符NULL)。

说明：返回指向第一次出现needle位置的指针，如果没找到则返回NULL。
```



