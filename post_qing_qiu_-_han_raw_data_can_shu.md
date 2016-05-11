# POST 請求 - 含 raw data 參數

以請求 https://api.github.com/rate_limit 這個 API 為例。

因為這 API 並沒有提供 POST 方式的請求，這裡僅是示範如何帶入參數並使用。

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {

    // 使用 @Body 將參數的值指定為 raw data 的內容，並指定 RequestBody 類型。
    public interface ApiUri {
        @POST("/rate_limit")
        Call<ResponseBody> post(@Body RequestBody body);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 建立 RequestBody 並設定 raw data 內容。
        String rawData = "{\"raw\":\"data\"}";
        MediaType json = MediaType.parse("application/json; charset=utf-8");
        RequestBody body = RequestBody.create(json, rawData);

        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .build();
        ApiUri apiUri = retrofit.create(ApiUri.class);
        Call<ResponseBody> call = apiUri.post(body);
        call.enqueue(new Callback<ResponseBody>() {
            @Override
            public void onResponse(Call<ResponseBody> call, Response<ResponseBody> response) {
                // 因為此 API 僅用 GET，不提供 POST 方法，所以會取得 404 狀態碼。
                int result = response.code();
                Log.d("MainActivity", result + "");
            }

            @Override
            public void onFailure(Call<ResponseBody> call, Throwable t) {
                t.printStackTrace();
            }
        });
    }
}
```