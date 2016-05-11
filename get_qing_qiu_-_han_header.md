# GET 請求 - 含 Header

以請求 https://api.github.com/rate_limit 這個 API 為例

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {

    public interface ApiUri {
        @GET("/rate_limit")
        //這個 API 其實不需特別設定這兩個 Header，這裡僅是示範如何加上 Header。
        @Headers({"Accept: application/json",
                "Content-Type: application/json"})
        Call<ResponseBody> get();
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .build();
        ApiUri apiUri = retrofit.create(ApiUri.class);
        Call<ResponseBody> call = apiUri.get();
        call.enqueue(new Callback<ResponseBody>() {
            @Override
            public void onResponse(Call<ResponseBody> call, Response<ResponseBody> response) {
                // 可透過 Response 取得發出的 request 物件，檢查是否有加入 Header。
                Log.d("MainActivity", response.raw().request().header("Accept"));
                Log.d("MainActivity", response.raw().request().header("Content-Type"));
            }

            @Override
            public void onFailure(Call<ResponseBody> call, Throwable t) {
                t.printStackTrace();
            }
        });
    }
}

```