# 非同步請求 - GET 方法

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {
    private TextView v;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //設定顯示畫面
        v = new TextView(this);
        setContentView(v);

        OkHttpClient client = new OkHttpClient();
        // 設定 Socket 嘗試連線時間上限
        client.setConnectTimeout(60, TimeUnit.SECONDS);
        // 設定 Socket 嘗試讀取時間上限
        client.setReadTimeout(60, TimeUnit.SECONDS);

        // 以 Google 網頁為例
        String url = "http://google.com.tw/";
        // 建立請求物件，設定網址
        Request request = new Request.Builder().url(url).build();
        // 以非同步方式執行請求，並定義 Callback 事件
        client.newCall(request).enqueue(new Callback() {
            @Override
            public void onFailure(Request request, final IOException e) {
                // 此方法不執行在主執行緒中，注意不能更新介面。
                String error = e.getMessage();
                // 顯示錯誤訊息
                updateText(error);
            }

            @Override
            public void onResponse(final Response response) {
                // 此方法不執行在主執行緒中，注意不能更新介面。
                try {
                    String result = "";
                    // 取得任一 HEADER
                    result += response.header("content-type") + "\n";
                    // 取得狀態碼
                    result += response.code() + "\n";
                    // 是否成功
                    result += response.isSuccessful() + "\n";
                    // 取得內容
                    result += response.body().string() + "\n";
                    // 顯示回傳訊息
                    updateText(result);
                } catch (IOException e) {
                    String result = "Load info fail.";
                    updateText(result);
                }

            }
        });
    }

    // 使用 View 的 post 方法，將介面更新執行在主執行緒中。
    private void updateText(final String text) {
        v.post(new Runnable() {
            @Override
            public void run() {
                v.setText(text);
            }
        });
    }
}
```