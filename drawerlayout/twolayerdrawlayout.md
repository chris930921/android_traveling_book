# TwoLayerDrawLayout 左側選單中的子選單

#### 排版
```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <android.support.v4.widget.DrawerLayout
        android:id="@+id/drawer_left"
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <TextView
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:text="左側滑出選單，點裡面的選項滑出右側選單" />

        <android.support.v4.widget.DrawerLayout
            android:id="@+id/drawer_right"
            android:layout_width="300dp"
            android:layout_height="match_parent"
            android:layout_gravity="left">

            <ListView
                android:id="@+id/left_option"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:background="#00FF00"
                android:choiceMode="singleChoice" />

            <ListView
                android:id="@+id/right_option"
                android:layout_width="300dp"
                android:layout_height="match_parent"
                android:layout_gravity="right"
                android:background="#0000FF"
                android:choiceMode="singleChoice" />

        </android.support.v4.widget.DrawerLayout>
    </android.support.v4.widget.DrawerLayout>
</RelativeLayout>
```

#### 程式
```java
public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        ListView leftList = (ListView) findViewById(R.id.left_option);
        ListView rightList = (ListView) findViewById(R.id.right_option);
        final DrawerLayout drawer1 = (DrawerLayout) findViewById(R.id.drawer_left);
        final DrawerLayout drawer2 = (DrawerLayout) findViewById(R.id.drawer_right);

        String[] values = new String[]{"Item 1", "Item 2", "Item 3", "Item 4", "Item 5",};
        ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, android.R.id.text1, values);
        leftList.setAdapter(adapter);
        rightList.setAdapter(adapter);

        leftList.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> adapterView, View view, int i, long l) {
                drawer2.openDrawer(Gravity.RIGHT);
            }
        });
        rightList.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> adapterView, View view, int i, long l) {
                drawer1.closeDrawer(Gravity.LEFT);
                drawer2.closeDrawer(Gravity.RIGHT);
            }
        });
    }
}
```
