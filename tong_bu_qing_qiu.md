# 同步請求

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 為了示範同步請求，這裡將主執行緒作網路請求的部份開啟，實務中並不這樣使用，因為會導致主執行緒卡住。
        StrictMode.ThreadPolicy policy = new StrictMode.ThreadPolicy.Builder().permitAll().build();
        StrictMode.setThreadPolicy(policy);

        String url = "http://google.com.tw/";
        Request request = new Request.Builder().url(url).build();
        OkHttpClient client = new OkHttpClient();

        try {
            // 使用 execute() 方法執行同步請求。
            Response response = client.newCall(request).execute();

            // 取回結果並設定畫面。
            TextView v = new TextView(this);
            v.setText(response.body().string());
            setContentView(v);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```