```
 buildTypes {
        release {
//            minifyEnabled false

            // 混淆
            minifyEnabled true
            // Zipalign优化
            zipAlignEnabled true
            // 移除无用的resource文件
            shrinkResources true
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
```



