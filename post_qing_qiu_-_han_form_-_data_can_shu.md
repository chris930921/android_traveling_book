# POST 請求 - 含 form-data 參數

以請求 https://api.github.com/rate_limit 這個 API 為例。

因為這 API 並沒有提供 POST 方式的請求，這裡僅是示範如何帶入參數並使用。

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {

    // 使用 @Field 指定以 form-data 的方式傳送參數
    public interface ApiUri {
        @POST("/rate_limit")
        Call<ResponseBody> auth(@Field("token") String token);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .build();
        ApiUri apiUri = retrofit.create(ApiUri.class);
        Call<ResponseBody> call = apiUri.auth("*************");
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