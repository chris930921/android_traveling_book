# onCreateOptionsMenu

用程式動態增加Item

```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        //新增 Menu Item，方法 menu.add(群組編號，Item編號，排序編號，顯示名稱);
        menu.add(0, 0, 0, "One");
        menu.add(0, 1, 2, "Two");
        menu.add(0, 2, 1, "Three");
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

![](picture/01.png)
