### 泛型（类型擦除）

JAVA中的泛型只是在程序源码中存在，在编译成字节码时就被替换为原生类型，并且在相应地方加上强制转换类型。

```
Map
```

```
<
Integer,String
>
 map = new HashMap
<
Integer,String
>
();  
map.put(1,"No.1");  
map.put(2,"No.2");  
System.out.println(map.get(1));  
System.out.println(map.get(2)); 
```





