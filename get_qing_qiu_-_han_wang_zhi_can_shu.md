# GET 請求 - 含網址參數

以請求 https://api.github.com/search/users?q=chris930921 這個 API 為例，

此搜尋使用者 API，有一個 q 網址參數代表要搜尋的關鍵字。

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends AppCompatActivity {

    public interface ApiUri {
        // 使用 @Query 代表加上網址參數，括號內輸入參數名稱，其後的 name 參數就代表其值。
        @GET("/search/users")
        Call<ResponseBody> searchUser(@Query("q") String name);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .build();

        ApiUri apiUri = retrofit.create(ApiUri.class);
        // 設定要搜尋的字串為 chris930921，取得一個 request 物件。
        Call<ResponseBody> call = apiUri.searchUser("chris930921");
        // 發出 Request。
        call.enqueue(new Callback<ResponseBody>() {
            @Override
            public void onResponse(Call<ResponseBody> call, Response<ResponseBody> response) {
                // 取得內容
                try {
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