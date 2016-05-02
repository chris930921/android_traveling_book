# 列出所有 Content Provider Uri



```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        String text = "";
        PackageManager pm = getPackageManager();
        // 取得全部含有 Provider 的 Package。
        List<PackageInfo> packageGroup = pm.getInstalledPackages(PackageManager.GET_PROVIDERS);
        // 歷遍全部 Package
        for (PackageInfo info : packageGroup) {
            // 取出 Provider 資訊
            ProviderInfo[] providers = info.providers;
            if (providers == null) {
                continue;
            }
            // 歷遍 Package 中全部的 Provider
            for (ProviderInfo provider : providers) {
                text += "content://" + provider.authority + "\n";
            }
        }
        // 設定畫面顯示
        TextView v = new TextView(this);
        v.setText(text);
        setContentView(v);
    }
}
```
