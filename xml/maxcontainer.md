## 初次開啟專案時，Android Project 會生成以下檔案

## activity_main.xml

```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin"
    tools:context=".MainActivity">

</RelativeLayout>

```
* xmlns:android 定義 android 前輟，讓標籤可以使用 **android:屬性名稱** 來設定元件或框架。
* xmlns:tools 定義 tools 前輟，讓標籤可以使用 **tools:屬性名稱** 來做額外設定。
* android:layout_width 最大框架 **寬度填滿 (match_parent)** 整個視窗。
* android:layout_height 最大框架 **高度填滿 (match_parent)** 整個視窗。
* android:paddingLeft、Right、Top、Bottom 設定 **框架邊框和內容有之間的內距**
* @dimen/activity_horizontal_margin Android 的預設內距大小。
* tools:context 



## MainActivity.java



```java

public class MainActivity extends ActionBarActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }


    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }
}

```
