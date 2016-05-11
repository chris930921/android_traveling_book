# 搭配 GSON - Get 請求處理 JSON 物件

以請求 https://api.github.com/rate_limit 這個 API 為例，其內容如下
```json
{
  "resources": {
    "core": {
      "limit": 60,
      "remaining": 48,
      "reset": 1462949064
    },
    "search": {
      "limit": 10,
      "remaining": 10,
      "reset": 1462948119
    }
  },
  "rate": {
    "limit": 60,
    "remaining": 48,
    "reset": 1462949064
  }
}
```

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends AppCompatActivity {

    // 根據 JSON 的結構和 key 的名稱，建立資料結構類別
    public class Data {
        public Rate rate;
    }

    // 根據 JSON 的結構和 key 的名稱，建立資料結構類別
    public class Rate {
        public int limit;
        public int remaining;
        public long reset;
    }

    // 在 interface 中設定 uri，在回傳值中指定該 uri 使用哪種資料結構
    public interface ApiUri {
        @GET("/rate_limit")
        Call<Data> get();
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Retrofit retrofit = new Retrofit.Builder()
                // 設定 host 位址
                .baseUrl("https://api.github.com")
                // 設定 使用 GSON 解析
                .addConverterFactory(GsonConverterFactory.create())
                .build();

        // 取得經 Annotation 處理過的 uri 物件
        ApiUri apiUri = retrofit.create(ApiUri.class);
        // 從 uri 物件產生 request 物件
        Call<Data> call = apiUri.get();
        // 設定 callback 並發出 request
        call.enqueue(new Callback<Data>() {
            @Override
            public void onResponse(Call<Data> call, Response<Data> response) {
                // 取得結果
                Log.d("MainActivity", response.body().rate.reset + "");
            }

            @Override
            public void onFailure(Call<Data> call, Throwable t) {
                t.printStackTrace();
            }
        });
    }
}

```