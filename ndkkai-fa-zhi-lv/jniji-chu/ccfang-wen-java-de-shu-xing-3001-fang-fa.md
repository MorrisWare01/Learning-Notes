#### 访问Java的非静态属性

```
JNIEXPORT void JNICALL
Java_com_win_ndksample_AccessField_accessInstanceField(
        JNIEnv *env, jclass type, jobject classField, jstring s_) {
    const char *s = (*env)->GetStringUTFChars(env, s_, 0);

    //通过对象拿到class
    jclass clz = (*env)->GetObjectClass(env, classField);
    //拿到对应属性ID
    jfieldID fid = (*env)->GetFieldID(env, clz, "str", "Ljava/lang/String;");
    //通过属性ID拿到属性的值
    jstring jstr = (*env)->GetObjectField(env, classField, fid);

    //将JAVA字符串转为c字符串
    const char *cstr = (*env)->GetStringUTFChars(env, jstr, NULL);
    //将传入的s叠加到属性变量后面
    char buff[50];
    sprintf(buff, "%s%s", cstr, s);

    //将C字符串转为JAVA字符串
    jstring jst_new = (*env)->NewStringUTF(env, buff);
    (*env)->SetObjectField(env, classField, fid, jst_new);

    (*env)->ReleaseStringUTFChars(env, jstr, cstr);
    (*env)->ReleaseStringUTFChars(env, s_, s);
}
```

#### 访问Java的静态属性

```
JNIEXPORT void JNICALL
Java_com_win_ndksample_AccessField_accessStaticField__I(JNIEnv *env, jclass type, jint num) {
    //通过完整类名拿到class
    jclass clz = (*env)->FindClass(env, "com/win/ndksample/ClassField");
    //拿到对应静态属性ID
    jfieldID fid = (*env)->GetStaticFieldID(env, clz, "num", "I");
    //通过静态属性ID拿到静态属性的值
    jint jnum = (*env)->GetStaticIntField(env, clz, fid);
    printf("Java num is %d", jnum);
    //通过静态属性ID修改静态属性的值
    (*env)->SetStaticIntField(env, clz, fid, num);
}
```

#### 访问JAVA的非静态方法

```

JNIEXPORT void JNICALL
Java_com_win_ndksample_AccessMethod_accessInstanceMethod(JNIEnv *env, jclass type,
                                                        jobject classField) {
    //通过对象实例找到class
    jclass clz = (*env)->GetObjectClass(env, classField);
    //通过class得到methodID
    jmethodID mID = (*env)->GetMethodID(env, clz, "instanceMethod", "()V");
    //通过mID调用Void方法
    (*env)->CallVoidMethod(env, classField, mID);

}
```

#### 访问JAVA的静态方法

```
JNIEXPORT void JNICALL
Java_com_win_ndksample_AccessMethod_accessStaticMethod(JNIEnv *env, jclass type) {

    //通过完整类名找到class
    jclass clz = (*env)->FindClass(env, "com/win/ndksample/ClassField");
    //通过class得到静态方法Id
    jmethodID mID = (*env)->GetStaticMethodID(env, clz, "staticMethod", "()V");
    //通过mID调用Void方法
    (*env)->CallStaticVoidMethod(env, clz, mID);
}
```

#### 访问JAVA父类方法

```
JNIEXPORT void JNICALL
Java_com_win_ndksample_AccessMethod_accessSuperMethod(JNIEnv *env, jclass type,
                                                      jobject classField) {
    //通过完整类名找到class
    jclass super_clz = (*env)->FindClass(env, "com/win/ndksample/SuperClass");
    //通过class找到方法id
    jmethodID mid = (*env)->GetMethodID(env, super_clz, "instanceMethod", "()V");

    //调用对象实例的方法实现
    (*env)->CallVoidMethod(env, classField, mid);
    //调用父类的方法实现
    (*env)->CallNonvirtualVoidMethod(env, classField, super_clz, mid);
}
```

使用CallVoidMethod，虽然传进去的是父类的Method ID，但是访问的让然是子类的实现。

通过CallNonvirtualVoidMethod，访问不覆盖的父类方法（C++使用virtual关键字来覆盖父类的实现），当然你也可以指定哪个父类（如果有多个父类的话）

####  访问JAVA类构造方法

```
JNIEXPORT jstring JNICALL
Java_com_win_ndksample_AccessMethod_accessConstructor(JNIEnv *env, jclass type) {
    //通过完整类名找到Date类
    jclass clz_date = (*env)->FindClass(env, "java/util/Date");
    //通过clz找到Date类构造方法
    jmethodID mid_date = (*env)->GetMethodID(env, clz_date, "<init>", "()V");

    //通过构造方法进行实例化对象
    jobject date = (*env)->NewObject(env, clz_date, mid_date);

    //通过clz找到Date的getTime方法
    jmethodID mid_getTime = (*env)->GetMethodID(env, clz_date, "toString", "()Ljava/lang/String;");
    //调用getTime方法
    jstring jtime = (*env)->CallObjectMethod(env, date, mid_getTime);
    
    return jtime;
}
```



