# 搭配 GSON - GET 請求處理整體 JSON 陣列

以請求 https://api.github.com/events 這個 API 為例，其內容如下
```json
[
  {
    "id": "3999090196",
    "type": "WatchEvent",
    "actor": {
      "id": 11425338,
      "login": "smalldu",
      "gravatar_id": "",
      "url": "https://api.github.com/users/smalldu",
      "avatar_url": "https://avatars.githubusercontent.com/u/11425338?"
    },
    "repo": {
      "id": 760732,
      "name": "ccgus/fmdb",
      "url": "https://api.github.com/repos/ccgus/fmdb"
    },
    "payload": {
      "action": "started"
    },
    "public": true,
    "created_at": "2016-05-11T08:39:28Z"
  },
  {
    ...其他 JSON 物件，這裡省略。
  }
]
```

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends Activity {

    // 根據陣列中的 JSON 物件的 key，設定資料結構類別。
    public class Event {
        public String id;
        public String type;
    }
    
    // 設定 uri
    public interface ApiUri {
        @GET("/events")
        Call<List<Event>> getEvent();
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .addConverterFactory(GsonConverterFactory.create())
                .build();

        ApiUri apiUri = retrofit.create(ApiUri.class);
        
        // 設定為 List<Event>，其會自動將 JSON 陣列轉為 List 結構，裡面每個元素就是 JSON 物件。
        Call<List<Event>> call = apiUri.getEvent();
        call.enqueue(new Callback<List<Event>>() {
            @Override
            public void onResponse(Call<List<Event>> call, Response<List<Event>> response) {
                // 取得 JSON 陣列內容。
                List<Event> eventGroup = response.body();
                // 取得 JSON 陣列長度。
                int size = eventGroup.size();
                // 訪問 JSON 陣列中所有 JSON 物件。
                for (int i = 0; i < size; i++) {
                    Log.d("MainActivity", eventGroup.get(i).id);
                    Log.d("MainActivity", eventGroup.get(i).type);
                }
            }

            @Override
            public void onFailure(Call<List<Event>> call, Throwable t) {
                t.printStackTrace();
            }
        });
    }
}

```