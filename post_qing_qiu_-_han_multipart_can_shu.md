# POST 請求 - 含 Multipart 參數

以請求 https://api.github.com/rate_limit 這個 API 為例。

因為這 API 並沒有提供 POST 方式的請求，這裡僅是示範如何帶入參數並使用。

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {

    public interface ApiUri {
        // @Multipart 設定請求使用 Multipart 方式
        // @Part 設定 Multipart 的參數名稱和值，並指定使用 RequestBody 類型。
        @Multipart
        @POST("/rate_limit")
        Call<ResponseBody> get(@Part("photo") RequestBody photo);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        RequestBody requestBody = null;
        try {
            // 讀取圖片檔案所有的二進位數值，正常的情境應是讀取檔案，這裡為求快速執行所以任選一張 Android 內建的圖片。
            // Android Studio 預期 openRawResource() 方法會讀取 R.raw 的資源，這裡加上 + 號我猜測是繞過檢查機制，避免錯誤訊息。
            InputStream in = getResources().openRawResource(+android.R.drawable.sym_def_app_icon);
            byte[] bytePhoto = new byte[in.available()];
            in.read(bytePhoto);
            // 建立 MultipartRequestBody，其內包含要上傳的圖片資料。
            requestBody = RequestBody.create(MediaType.parse("application/octet-stream"), bytePhoto);
        } catch (IOException e) {
            e.printStackTrace();
        }

        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .build();
        ApiUri apiUri = retrofit.create(ApiUri.class);
        Call<ResponseBody> call = apiUri.get(requestBody);
        call.enqueue(new Callback<ResponseBody>() {
            @Override
            public void onResponse(Call<ResponseBody> call, Response<ResponseBody> response) {
                // 因為此 API 僅使用 GET，不提供 POST 方法，所以會取得 404 狀態碼。
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