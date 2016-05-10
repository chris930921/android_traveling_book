# 以 Stream 方式讀取內容

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

        String url = "http://google.com.tw/";
        Request request = new Request.Builder().url(url).build();
        OkHttpClient client = new OkHttpClient();
        client.newCall(request).enqueue(new Callback() {
            @Override
            public void onFailure(Request request, final IOException e) {
                e.printStackTrace();
            }

            @Override
            public void onResponse(final Response response) {
                try {
                    // 設定緩衝區大小
                    byte[] buffer = new byte[1024];
                    
                    // 取得輸入流
                    InputStream input = response.body().byteStream();
                    
                    // 儲存不定數量的 byte 陣列，最後再一次寫出轉成字串，
                    // 通常是因為要寫入檔案才用 Stream 讀取，這裡為求簡化而使用此方式。
                    ByteArrayOutputStream byteBuilder = new ByteArrayOutputStream();
                    while (input.read(buffer) != -1) {
                        byteBuilder.write(buffer);
                    }
                    
                    // 將所有內容以 byte 陣列轉出，再使用 String 的建構式轉為字串。
                    String result = new String(byteBuilder.toByteArray());
                    Log.d("MainActivity", result);
                
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        });
    }
}
```