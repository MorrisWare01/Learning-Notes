### 关于属性与方法的签名

#### 属性的签名

属性的签名其实就是属性的类型的简称，对应关系如下：

| Java Language Type | Field Description |
| :--- | :--- |
| boolean | **Z** |
| byte | B |
| char | C |
| short | S |
| int | I |
| long | **J** |
| float | F |
| double | D |
| void | V |
| object | **L完整包名; 例如：String -&gt; Ljava/lang/String;** |
| Array | **\[元素签名 例如int\[\] -&gt; \[I , int\[\]\[\] -&gt; \[\[I** |

#### 方法的签名

```
(参数类型签名)返回值类型签名
```

| Java Language Type | Method Description |
| :--- | :--- |
| String f\(int i,String s\); | \(ILjava/lang/String;\)Ljava/lang/String; |
| String\(byte\[\] bytes\); | \(\[B\)V |

#### 获得指定类的所有属性、方法的签名

```
javap -s -p 完整类名
```



