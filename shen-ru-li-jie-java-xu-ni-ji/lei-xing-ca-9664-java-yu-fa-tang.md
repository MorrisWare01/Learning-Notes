### 泛型（类型擦除）

JAVA中的泛型只是在程序源码中存在，在编译成字节码时就被替换为原生类型，并且在相应地方加上强制转换类型。

下面是一段简单的 Java 泛型代码：

```
Map<Integer,String>map = new HashMap<Integer,String>();  
map.put(1,"No.1");  
map.put(2,"No.2");  
System.out.println(map.get(1));  
System.out.println(map.get(2));
```

将这段 Java 代码编译成 Class 文件，然后再用字节码反编译工具进行反编译后，将会发现泛型都变回了原生类型，如下面的代码所示：

```
Map map = new HashMap();  
map.put(1,"No.1");  
map.put(2,"No.2");  
System.out.println((String)map.get(1));  
System.out.println((String)map.get(2));
```

### 特征签名

Java方法特征签名：包括了方法名称、参数顺序和参数类型，并不包括方法的返回值。

字节码特征签名：除了包括了方法名称、参数顺序和参数类型，还包括方法返回值及受查异常表。

