单例模式：保证类在内存中只存在一个实例。

### 双重检测锁

```
public class Singleton {
    private volatile static Singleton INSTANCE = null;

    private Singleton(){   
    }

    public static Singleton getInstance(){
        if(INSTANCE == null){
            synchronized(Singleton.class){
                if(INSTANCE == null){
                    INSTANCE = new Singleton();
                }
            }
        }
        return INSTANCE;
    }

}
```

#### 用volatile的原因

INSTANCE = new Singleton\(\)并非原子操作，执行该语句jvm做了三件事

1. 给INSTANCE分配内存
2. 调用Singleton的构造函数来初始化成员变量
3. 将INSTANCE对象指向分配的内存空间（这时的INSTANCE才不为null）

由于JVM的即时编译器存在**指令重排序**的优化，导致2和3的顺序不能被保证，最终的执行顺序可能是1-2-3或1-3-2.在第二种情况下，当3执行完毕，2未执行时被另外线程抢占，将导致INSTANCE还没初始化就被返回，从而抛出异常。

而volatile关键词的功能为禁止指定重排序优化。

### 饿汉式

```
public class Singleton{
    //类加载时就初始化
    private static final Singleton instance = new Singleton();
    
    private Singleton(){}
    public static Singleton getInstance(){
        return instance;
    }
}
```

### 静态内部类

```
public class Singleto{
    private static class SingletonHolder{
        private static final Singleton INSTANCE = new Singleton();
    }

    private Singleton(){

    }

    public static final Singleton getInstance(){
        return SingletonHolder.INSTANCE;
    }

}
```



