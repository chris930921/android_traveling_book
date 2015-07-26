# Android 教學

### 撰寫這個 Android 教學希望達到以下目的:

* 讀者可以馬上抓到現有的範例。
* Sample Code 容易複製貼上後無痛執行。
* Sample Code 盡量不分散到多個檔案。
* 做內部訓練或上課教學，學員容易找到教材並執行。
* 提供學員課後複習也能找到資料。
* 資料保存與推廣。
* 容易更新資料，提供新事物的試驗結果。


### Java 名詞定義

```java
//類別修飾詞 class 類別名稱 extends 父類別名稱 implements 介面名稱
public class MainActivity extends Activity implements OnClickListener{

    //屬性修飾詞  屬性型態  屬性名稱 = 屬性賦值;
    private int field = 0;

    //靜態屬性
    private static int staticField = 0;

    //類別常數
    private final int FINAL_FIELD = 0;

    //建構式修飾詞  類別建構式(建構式參數  參數名稱){ 建構式程式區塊 }
    public MainActivity(){
        //父類別建構式
        super();
    }

    //方法修飾詞  方法回傳值  方法名稱 (方法參數  參數名稱){方法程式區塊}
    public void onCreate(Bundle savedInstanceState){
        //父類別方法
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        //宣告區域變數
        int field = 0;

        //建立 Object 型態物件參考
        Object object;

        //建立 Object 型態物件
        object = new Object();
    }
}
```
