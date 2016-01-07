# Cucumber-jvm

* Android Module build.gradle:

```gradle
android {
    defaultConfig {
        // 假設 id 是 com.packagename
        applicationId com.packagename
        ...
        // 設定測試應用程式的 applicationId，之後需建立對應的 package。
        testApplicationId applicationId + ".test"
        // 設定哪個測試類別要加入測試流程中，這裡使用 cucumber 提供的 Instrumentation。
        testInstrumentationRunner "cucumber.api.android.CucumberInstrumentation"
    }
    // 設定測試應用程式的 assets，使用哪個路徑替代
    // 目的是可以分離出測試用檔案到替代的 assets 資料夾
    sourceSets {
        androidTest {
            assets.srcDirs = ['src/androidTest/assets']
        }
    }
    ...
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    // 最新的版本 1.2.4 一直無法執行成功，這裡使用較舊的 1.2.0 版本。
    androidTestCompile 'info.cukes:cucumber-android:1.2.0@jar'
    // cucumber-android 不使用 @jar 包起來的話，編譯時會出現
    // com.android.dx.cf.iface.ParseException: bad class file magic (cafebabe) or version (0034.0000)
    androidTestCompile 'info.cukes:cucumber-picocontainer:1.2.0'
    
    androidTestCompile 'info.cukes:cucumber-core:1.2.0'
    androidTestCompile 'info.cukes:cucumber-html:0.2.3'
    androidTestCompile 'info.cukes:cucumber-java:1.2.0'
    androidTestCompile 'info.cukes:cucumber-junit:1.2.0'
    androidTestCompile 'info.cukes:cucumber-jvm-deps:1.0.3'
    androidTestCompile 'info.cukes:gherkin:2.12.2'
    androidTestCompile 'junit:junit:4.12'
}

```

* 在 Android Studio Module 中建立以下兩種資料夾路徑 


```java
// 放置 feature 檔案的地方
src/androidTest/assets/
// build.gradle 裡 testApplicationId 欄位對應的 package
src/androidTest/com/packagename/test
```

##### Troubleshooting：
```
使用 info.cukes:cucumber-android:1.2.4 執行 gradle Task preDebugAndroidTest 時出現：
com.android.dx.cf.iface.ParseException: bad class file magic (cafebabe) or version (0034.0000)
---

此訊息指出使用 Java 1.8 版本(0034.0000)。
且要是 Java 編譯(cafebabe)而非 Android，所以 info.cukes:cucumber-android:1.2.4 項目需用@jar先包成jar檔案。
```

