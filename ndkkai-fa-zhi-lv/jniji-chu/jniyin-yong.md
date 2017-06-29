#### 局部引用

通过NewLocalRef和各种JNI接口创建（FindClass、NewObject、GetObjectClass和NewCharArray等）。

会阻止GC回收所引用的对象，不能在本地函数中跨函数使用。

函数返回后局部引用所引用的对象会被JVM 自动释放，或调用 DeleteLocalRef 释放。

```
(*env)->DeleteLocalRef(env,local_ref)
```

#### 全局引用

调用 NewGlobalRef 基于局部引用创建。

会阻 GC 回收所引用的对象，可以跨方法、跨线程使用。

JVM 不会自动释放，必须调用 DeleteGlobalRef 手动释放。

```
(*env)->DeleteGlobalRef(env,global_ref)
```

#### 弱全局引用

调用 NewWeakGlobalRef 基于局部引用或全局引用创建。

不会阻止 GC 回收所引用的对象，可以跨方法、跨线程使用。

引用不会自动释放，在 JVM 认为应该回收它的时候（比如内存紧张的时候）进行回收而被释放。

或调用DeleteWeakGlobalRef 手动释放。

```
(*env)->DeleteWeakGlobalRef(env,g_cls_string)
```



