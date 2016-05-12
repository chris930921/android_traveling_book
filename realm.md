# Realm

build.gradle
```gradle
    compile 'io.realm:realm-android:0.87.5'
```

trobleshooting
```text
Error:(43, 16) error: The fields of the RealmObject class must be private
繼承 RealmObject 的類別，其屬性修飾詞不可為 public。
```

```text
Error:(73, 17) error: Setter setXXXXXX is not associated to any field
繼承 RealmObject 的類別，其內有一個 setter 方法無法對應到任何屬性。
```

```text
Error:(17, 12) error: The RealmClass annotation does not support nested classes
繼承 RealmObject 的類別，不可宣告在其他類別中。
```

```text
Error:(6, 17) error: DataTable is not public in com.realm; cannot be accessed from outside package
繼承 RealmObject 的類別，可能因為修飾詞或是宣告位置的關係，無法被外部 package 存取。
```