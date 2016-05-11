# 搭配 GSON - GET 請求處理屬性中的 JSON 陣列

以請求 https://api.github.com/search/users?q=chris930921 這個 API 為例，其內容如下

目標是解析 items 這個含有 JSON 陣列的屬性。
```json
{
  "total_count": 1,
  "incomplete_results": false,
  "items": [
    {
      "login": "chris930921",
      "id": 7033275,
      "avatar_url": "https://avatars.githubusercontent.com/u/7033275?v=3",
      "gravatar_id": "",
      "url": "https://api.github.com/users/chris930921",
      "html_url": "https://github.com/chris930921",
      "followers_url": "https://api.github.com/users/chris930921/followers",
      "following_url": "https://api.github.com/users/chris930921/following{/other_user}",
      "gists_url": "https://api.github.com/users/chris930921/gists{/gist_id}",
      "starred_url": "https://api.github.com/users/chris930921/starred{/owner}{/repo}",
      "subscriptions_url": "https://api.github.com/users/chris930921/subscriptions",
      "organizations_url": "https://api.github.com/users/chris930921/orgs",
      "repos_url": "https://api.github.com/users/chris930921/repos",
      "events_url": "https://api.github.com/users/chris930921/events{/privacy}",
      "received_events_url": "https://api.github.com/users/chris930921/received_events",
      "type": "User",
      "site_admin": false,
      "score": 62.297253
    }
  ]
}
```

AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

MainActivity.java
```java
public class MainActivity extends AppCompatActivity {
    
    // 整個 JSON 物件中有一個 items 屬性，內容為 JSON 陣列，可依以下方式設定資料結構類別。
    public class SearchUser {
        public List<Item> items = new ArrayList<Item>();
    }

    public class Item {
        public int id;
        // 遇到以底線隔開的名稱(html_url)，可以用小駝峰取代，GSON 會自動處理。
        public String htmlUrl;
        public boolean siteAdmin;
        public float score;
    }

    public interface ApiUri {
        // 使用 @Query 代表加上 GET 參數，括號內輸入參數名稱，其後的 name 參數就代表其值。
        @GET("/search/users")
        Call<SearchUser> searchUser(@Query("q") String name);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("https://api.github.com")
                .addConverterFactory(GsonConverterFactory.create())
                .build();

        ApiUri apiUri = retrofit.create(ApiUri.class);
        Call<SearchUser> call = apiUri.searchUser("chris930921");
        call.enqueue(new Callback<SearchUser>() {
            @Override
            public void onResponse(Call<SearchUser> call, Response<SearchUser> response) {
                // 取得內容
                SearchUser searchUser = response.body();
                int size = searchUser.items.size();
                // 訪問陣列中的所有元素。
                for (int i = 0; i < size; i++) {
                    Log.d("MainActivity", searchUser.items.get(i).htmlUrl);
                    Log.d("MainActivity", searchUser.items.get(i).siteAdmin + "");
                    Log.d("MainActivity", searchUser.items.get(i).score + "");
                }
            }

            @Override
            public void onFailure(Call<SearchUser> call, Throwable t) {
                t.printStackTrace();
            }
        });
    }
}

```