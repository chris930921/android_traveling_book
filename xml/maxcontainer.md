## 初次開啟專案時，Android Project 會生成以下檔案

#### activity_main.xml

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
* xmlns:android
* 定義 android 前輟，讓標籤可以使用 **android:屬性名稱** 來設定元件或框架。
* -
* xmlns:tools
* 定義 tools 前輟，讓標籤可以使用 **tools:屬性名稱** 來做額外設定。
* -
* android:layout_width
* 最大框架 **寬度填滿 (match_parent)** 整個視窗。
* -
* android:layout_height
* 最大框架 **高度填滿 (match_parent)** 整個視窗。
* -
* android:paddingLeft、Right、Top、Bottom
* 設定 **框架邊框和內容之間的內距**
* -
* @dimen/activity_horizontal_margin
* Android 的**預設內距大小**。
* -
* tools:context
* 提供**設計階段**時，讓 xml 套用 AndroidManifest.xml 中設定的樣式，並**顯示在介面預覽畫面**中。



#### MainActivity.java

```java
//宣告這個 Class 為 Activity，可用來顯示畫面。
public class MainActivity extends ActionBarActivity {

    @Override //此畫面的程式進入點
    protected void onCreate(Bundle savedInstanceState) {
        //先執行父類別中的onCreate方法。
        super.onCreate(savedInstanceState);
        //用 R.layout.介面xml名稱設定畫面，來指定這個Activity要套用哪一個XML檔案來顯示介面。
        setContentView(R.layout.activity_main);
    }


    @Override // ActionBar 的 Menu 初始化方法
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override // 每個 Menu Item 被點擊時執行的方法
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
