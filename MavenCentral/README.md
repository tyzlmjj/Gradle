# 上传Android library到MavenCentral

### **Step 1**
在Project的`build.gradle`文件的顶部添加插件
```gradle
plugins {
    id("io.github.gradle-nexus.publish-plugin") version "1.1.0"
}
```

在Project的`build.gradle`文件的底部添加引用
```gradle
apply from: 'https://raw.githubusercontent.com/tyzlmjj/Gradle/master/MavenCentral/publish-root.gradle'
```

### **Step 2**

在Module的`build.gradle`文件的最后加上如下代码，这是一个例子，里面的内容根据实际情况填写

```gradle
ext {

    libraryName = 'PagerBottomTabStrip'
    libraryDescription = 'An navigation bar for Android'

    publishedGroupId = 'me.majiajie'
    artifact = 'pager-bottom-tab-strip'

    siteUrl = 'https://github.com/tyzlmjj/PagerBottomTabStrip'
    scmUrl = 'github.com/tyzlmjj/PagerBottomTabStrip.git'

    libraryVersion = rootProject.ext.versionName

    developerId = 'tyzlmjj'
    developerName = 'Ma JiaJie'
    developerEmail = 'tyzl931019@gmail.com'

    licenseName = 'The Apache Software License, Version 2.0'
    licenseUrl = 'http://www.apache.org/licenses/LICENSE-2.0.txt'
}

// 如果是没有引入Kotlin的项目就使用publish_module.gradle
apply from: 'https://raw.githubusercontent.com/tyzlmjj/Gradle/master/MavenCentral/publish_module_kotlin.gradle'
```

### **Step 3**

在根目录下的`local.properties`文件中添加以下参数

```
signing.keyId=[GPG指纹]
signing.password=[GPG密码]
signing.secretKeyRingFile=[GPG私钥文件]
ossrhUsername=[中央库账号]
ossrhPassword=[中央库密码]
sonatypeStagingProfileId=[中央库登录账号后的ProfileId]
```

### **Step 4**

上传文件到中央库
```
gradle publishReleasePublicationToSonatypeRepository
```

关闭中央库的临时存储并发布
```
gradle closeAndReleaseSonatypeStagingRepository
```
