### JNI数据类型

#### 基本数据

Java基本数据类型与JNI数据类型的映射关系

```
Java类型->JNI类型->C类型
```

JNI的基本数据类型有（左边是Java，右边是JNI）：

| Java Language Type | Native Type | Description |
| :--- | :--- | :--- |
| boolean | jboolean | unsigned 8 bits |
| byte | jbyte | signed 8 bits |
| char | jchar | unsigned 16 bits |
| short | jshort | signed 16bits |
| int | jint | signed 32bits |
| long | jlong | signed 64bits |
| float | jfloat | 32bits |
| double | jdouble | 64bits |
| void | void | void |

#### 引用类型\(对象\)

```
String                 jstring
Object                 jobject

数组,基本数据类型的数组
byte[]                 jByteArray
对象数组
object[](String[])     jobjectArray
```

### native函数参数说明

每个native函数，都至少有两个参数（JNIEnv\*,jclass或者jobject\)。

1）当native方法为静态方法时：  
jclass 代表native方法所属类的class对象\(JniTest.class\)。

2）当native方法为非静态方法时：  
jobject 代表native方法所属的对象。

###### native函数的头文件可以自己写。

### 



