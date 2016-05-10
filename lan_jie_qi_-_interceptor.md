# 攔截器 - Interceptor

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

        // 以需身份驗證的 API 為例，用攔截器將所有請求的 HEADER
        // 自動加上 TOKEN 來通過驗證，可減少重複的程式碼。
        Interceptor interceptor = new Interceptor() {
            @Override
            public Response intercept(Chain chain) throws IOException {
                Request oldRequest = chain.request();
                
                // 建立相同的 Request 並加上 HEADER。
                Request newRequest = oldRequest.newBuilder().addHeader("X-AUTH-TOKEN", "****************").build();
                
                // 發出請求，並將結果回傳。
                Response response = chain.proceed(newRequest);
                return response;
            }
        };
        OkHttpClient client = new OkHttpClient();
        
        // 加入攔截器
        client.networkInterceptors().add(interceptor);

        String url = "http://google.com.tw/";
        Request request = new Request.Builder().url(url).build();
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
                    Log.d("MainActivity", result);
                
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        });
    }
}
```