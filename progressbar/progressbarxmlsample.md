# XML範例

#### 圓形風格

```xml
 <ProgressBar
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_gravity="center_vertical" />
```

#### 大圓形風格
```xml
<ProgressBar
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_gravity="center_vertical"

    style="?android:attr/progressBarStyleLarge"/>
```

#### 小圓形風格
```xml
<ProgressBar
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_gravity="center_vertical"

    style="?android:attr/progressBarStyleSmall"/>
```

#### 標題型風格
```xml
<ProgressBar
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_gravity="center_vertical"

    style="?android:attr/progressBarStyleSmallTitle"/>
```

#### 長條型風格
```xml
<ProgressBar
    android:layout_width="match_parent"
    android:layout_height="100dip"

    style="?android:attr/progressBarStyleHorizontal"/>
```

#### 設定進度，預設最大值是100。
```xml
<ProgressBar
    style="?android:attr/progressBarStyleHorizontal"
    android:layout_width="match_parent"
    android:layout_height="100dip"
    android:progress="50" />
```

#### 修改最大值
```xml
<ProgressBar
    style="?android:attr/progressBarStyleHorizontal"
    android:layout_width="match_parent"
    android:layout_height="100dip"
    android:progress="50"

    android:max="200"/>
```

### 第二進度條
```xml
<ProgressBar
    style="?android:attr/progressBarStyleHorizontal"
    android:layout_width="match_parent"
    android:layout_height="100dip"
    android:max="100"
    android:progress="50"

    android:secondaryProgress="75" />
```
* 長條型進度條才能設置
* 常用於影片緩衝的讀取進度
