# GET 請求 - 無參數

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {

    // 在 interface 中設定 uri，在回傳值中指定該 uri 使用哪種資料結構
    public interface ApiUri {
        @GET("/rate_limit")
        Call<ResponseBody> get();
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 設定 host 位址
        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .build();
        // 取得經 Annotation 處理過的 uri 物件
        ApiUri apiUri = retrofit.create(ApiUri.class);
        // 從 uri 物件產生 request 物件，指定內容的形式為 ResponseBody，可取得完整的內容字串。
        Call<ResponseBody> call = apiUri.get();
        // 設定 callback 並發出 request
        call.enqueue(new Callback<ResponseBody>() {
            @Override
            public void onResponse(Call<ResponseBody> call, Response<ResponseBody> response) {
                try {
                    // 取得結果
                    String result = response.body().string();
                    Log.d("MainActivity", result);
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }

            @Override
            public void onFailure(Call<ResponseBody> call, Throwable t) {
                t.printStackTrace();
            }
        });
    }
}

```