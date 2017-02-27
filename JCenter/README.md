
# 上传Android library到中央库

### **Step 1**
在Module的`build.gradle`文件的顶部添加两个插件
```gradle
plugins {
    id "com.jfrog.bintray" version "1.7.3"
    id "com.github.dcendents.android-maven" version "1.5"
}
```
### **Step 2**

在Module的`build.gradle`文件的最后加上如下代码，这是一个例子，里面的内容根据实际情况填写

```gradle
ext {
    bintrayRepo = 'maven'
    bintrayName = 'pager-bottom-tab-strip'

    publishedGroupId = 'me.majiajie'
    libraryName = 'PagerBottomTabStrip'
    artifact = 'pager-bottom-tab-strip'

    libraryDescription = 'A bottom navigation bar for Android'

    siteUrl = 'https://github.com/tyzlmjj/PagerBottomTabStrip'
    gitUrl = 'https://github.com/tyzlmjj/PagerBottomTabStrip.git'

    libraryVersion = '1.0.0'

    developerId = 'tyzlmjj'
    developerName = 'Ma JiaJie'
    developerEmail = 'tyzl931019@gmail.com'

    licenseName = 'The Apache Software License, Version 2.0'
    licenseUrl = 'http://www.apache.org/licenses/LICENSE-2.0.txt'
    allLicenses = ["Apache-2.0"]
}

apply from: 'https://raw.githubusercontent.com/tyzlmjj/Gradle/master/JCenter/maven_install.gradle'
apply from: 'https://raw.githubusercontent.com/tyzlmjj/Gradle/master/JCenter/bintray.gradle'

```

### **Step 3**

在根目录下的`local.properties`文件中添加以下参数
```
bintray.user=[JCenter用户名]
bintray.apikey=[JCenter 账户的 APIkey]
bintray.gpg.password=[GPG密码]
```




