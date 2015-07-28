# Log

* 常用來將程式執行的結果，紀錄在手機並透過 SDK 印出到電腦上，以判斷程式是否出錯。
* 可以設定 5 種等級，不同等級代表不同資訊。
* 可以設定 TAG 字串來過濾資訊，因為電腦會抓出所有 Log，必須找出自己想看的 Log 。


* VERBOSE 詳細訊息
* 主要運用在開發時，會紀錄一些次數頻繁、但重要性較低的訊息。
* **使用 Log.v ( tag , msg );**


* DEBUG 除錯訊息
* 主要提供給開發人員，用來確認邏輯是否正確、流程是否正常，或是一些其他開發中需要的用途。
* **使用 Log.d ( tag , msg );**


* INFO 通知訊息
* 紀錄重要程序的狀態，目前程序執行到哪個階段、任務是否完成。
* **使用 Log.i ( tag , msg );**


* WARN 警告訊息
* 紀錄可能會引發錯誤的警告訊息，或是已經產生錯誤，但不會導致 APP 崩潰的訊息。
* **使用 Log.w ( tag , msg );**


* ERROR 錯誤訊息
* 紀錄導致 APP 崩潰閃退的訊息。
* **使用 Log.e ( tag , msg );**


## 印出目前程序狀態
```java
public class MainActivity extends Activity{

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Log.i("AppLogTest", "onCreate 執行完畢.");
    }
}

```

## 判斷進入流程
```java
public class MainActivity extends Activity{

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        int random = (int)(Math.random()*100);

        Log.i("AppLogTest", "開始判斷");
        if(random %2 == 0){
            Log.i("AppLogTest", "偶數");
        }else{
            Log.i("AppLogTest", "奇數");
        }

    }
}

```

## 印出變數
```java
public class MainActivity extends Activity{

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        int random = (int)(Math.random()*100);
        Log.i("AppLogTest", "亂數值: " + random );
    }
}
```

