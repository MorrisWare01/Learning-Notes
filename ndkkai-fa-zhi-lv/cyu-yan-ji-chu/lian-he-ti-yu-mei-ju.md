### 联合体（共用体）

不同类型的变量共同占用一段内存（相互覆盖），联合变量任何时刻只有一个成员存在，节省内存

联合体变量的大小=最大的成员所占的字节数（字节对齐 ）

```
#include <stdio.h>

union MyValue{
    unsigned int n;
    unsigned char x[2];
};

void main(){
    union MyValue v;
    v.n = 65535; 

    printf("%d,%d,%d\n", v.n, v.x[1], v.x[0]);
}
```

JNI头文件中的联合体：

```
typedef union jvalue {
    jboolean    z;
    jbyte       b;
    jchar       c;
    jshort      s;
    jint        i;
    jlong       j;
    jfloat      f;
    jdouble     d;
    jobject     l;
} jvalue;
```

### 枚举（enumeration）

枚举（列举所有的情况），限定值的取值范围，保证取值的安全性。

```
enum Day{
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday
};

void main(){
    enum Day d = Tuesday;

    printf("%#x,%d\n", &d, d);
    system("pause");
}
```



