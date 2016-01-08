# ViewPagger

* Android Studio Module build.gradle

```gradle
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.android.support:support-v13:23.+'
}
```


* Troubleshooring

```
執行時，出現以下錯誤導致 App 崩潰
android.content.res.Resources$NotFoundException: Unable to find resource ID #0xffffffff
        at android.content.res.Resources.getResourceName(Resources.java:2026)
---

因為建立 ViewPager 之後沒有設定 Id，可如下方式撰寫。

ViewPager pager = new ViewPager(this);
pager.setId(View.generateViewId());
```
