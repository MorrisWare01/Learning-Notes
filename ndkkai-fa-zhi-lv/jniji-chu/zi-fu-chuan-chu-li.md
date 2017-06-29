#### 获取和释放以UTF-8格式编码的字符串

```
原型：const char* (*GetStringUTFChars)(JNIEnv*, jstring, jboolean*);

功能：把一个 jstring 指针（指向 JVM 内部的 Unicode 字符序列）转换成一个UTF-8 格式的 C 字符串。

说明：jboolean*：取值 JNI_TRUE 和 JNI_FALSE，如果值为 JNI_FALSE，表示返回 JVM 内部源字符串的指针;

如果值为 JNI_TRUE，表示返回 JVM 内部源字符串的一份拷贝，并为新产生的字符串分配内存空间。

返回：内存分配成功返回指向新地址的指针，内存分配失败返回NULL

注意：不要忘记安全检查
```

```
原型：void (*ReleaseStringUTFChars)(JNIEnv*, jstring, const char*);

功能：释放GetStringUTFChars 内存分配的内存。

说明：调用 GetStringUTFChars 函数从 JVM 内部获取一个字符串之后，
JVM 内部会分配一块新的内存，用于存储源字符串的拷贝，以便本地代码访问和修改。
```

```
原型：jstring (*NewStringUTF)(JNIEnv*, const char*);

功能：构建一个新的 java.lang.String 字符串对象，这个新创建的字符串会自动转换成 Java 支持的 Unicode 编码。

说明：如果 JVM 不能为构造 java.lang.String 分配足够的内存，NewStringUTF 会抛出一个 OutOfMemoryError 异常，并返回 NULL。

返回：分配成功返回jstring对象，分配失败返回NULL
```

```
原型：jsize (*GetStringUTFLength)(JNIEnv*, jstring);

功能：获取utf-8编码的jstring字符串的长度
```

#### 获取和释放以 Unicode 格式编码的字符串

```
原型：const jchar* (*GetStringChars)(JNIEnv*, jstring, jboolean*);

功能：把一个 jstring 指针（指向 JVM 内部的 Unicode 字符序列）转换成一个unicode格式的jchar指针。

返回：内存分配成功返回指向新地址的指针，内存分配失败返回NULL
```

```
原型：void (*ReleaseStringChars)(JNIEnv*, jstring, const jchar*);

功能：释放GetStringChars 内存分配的内存。
```

```
原型：jstring (*NewString)(JNIEnv*, const jchar*, jsize);

功能：构建一个新的 java.lang.String 字符串对象，这个新创建的字符串会自动转换成 Java 支持的 Unicode 编码。
```

```
原型：jsize (*GetStringLength)(JNIEnv*, jstring);

功能：获取unicode编码的jstring字符串的长度
```



