# GET 請求 - 含 URI 參數

以請求 https://api.github.com/users/chris930921 這個 API 為例

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {

    public interface ApiUri {
        
        // 設定 uri 為 https://api.github.com/users/{user}
        @GET("/users/{user}")
        
        // 使用 @Path("user") 將參數的值取代 {user}。
        Call<ResponseBody> getUser(@Path("user") String user);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .build();
        ApiUri apiUri = retrofit.create(ApiUri.class);
        
        // 所以這裡實際存取的網址為 https://api.github.com/users/chris930921
        Call<ResponseBody> call = apiUri.getUser("chris930921");
        call.enqueue(new Callback<ResponseBody>() {
            @Override
            public void onResponse(Call<ResponseBody> call, Response<ResponseBody> response) {
                try {
                    
                    // 取得使用者資訊
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