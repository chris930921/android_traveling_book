# 非同步請求 - POST 方法 - RawData 參數

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

        OkHttpClient client = new OkHttpClient();
        client.setConnectTimeout(60, TimeUnit.SECONDS);
        client.setReadTimeout(60, TimeUnit.SECONDS);

        // 設定 raw data 參數
        String value = "{\"account\":\"admin\",\"password\":\"admin\"}";
        MediaType json = MediaType.parse("application/json; charset=utf-8");
        RequestBody params = RequestBody.create(json, value);

        // 建立請求物件，設定網址
        String url = "http://google.com.tw/";
        Request request = new Request.Builder().post(params).url(url).build();

        client.newCall(request).enqueue(new Callback() {
            @Override
            public void onFailure(Request request, final IOException e) {
                e.printStackTrace();
            }

            @Override
            public void onResponse(final Response response) {
                try {
                    // 取得內容
                    String result = response.body().string();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        });
    }
}
```