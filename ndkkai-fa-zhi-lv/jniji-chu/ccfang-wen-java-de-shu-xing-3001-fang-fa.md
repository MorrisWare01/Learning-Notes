#### 访问Java的非静态属性

```
//通过对象实例拿到class
jclass clz = (*env)->GetObjectClass(env, classField);
//通过class拿到对应属性ID
jfieldID fid = (*env)->GetFieldID(env, clz, "str", "Ljava/lang/String;");
//通过对象实例和属性ID拿到属性的值
jstring jstr = (*env)->GetObjectField(env, classField, fid);
//通过对象实例、属性id和新值修改属性的值
(*env)->SetObjectField(env, classField, fid, jst_new);
```

#### 访问Java的静态属性

```
//通过完整类名拿到class
jclass clz = (*env)->FindClass(env, "com/win/ndksample/ClassField");
//拿到对应静态属性ID
jfieldID fid = (*env)->GetStaticFieldID(env, clz, "num", "I");
//通过静态属性ID拿到静态属性的值
jint jnum = (*env)->GetStaticIntField(env, clz, fid);
printf("Java num is %d", jnum);
//通过静态属性ID修改静态属性的值
(*env)->SetStaticIntField(env, clz, fid, num);
```



