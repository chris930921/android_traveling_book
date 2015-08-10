# ProgressDrialog 視窗

#### 一般型
```java
public class MainActivity extends Activity {
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        ProgressDialog dialog = new ProgressDialog(this);
        dialog.setTitle("標題");
        dialog.setMessage("等待中...");
        dialog.show();
    }
}
```

#### 長條滾動型
```java
public class MainActivity extends Activity {
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        ProgressDialog dialog = new ProgressDialog(this);
        //設定風格
        dialog.setProgressStyle(ProgressDialog.STYLE_HORIZONTAL);
        //是否重複滾動
        dialog.setIndeterminate(true);
        dialog.show();
    }
}
```

#### 設定進度
```java
public class MainActivity extends Activity {
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        ProgressDialog dialog = new ProgressDialog(this);
        dialog.setProgressStyle(ProgressDialog.STYLE_HORIZONTAL);
        // 關閉重複滾動
        dialog.setIndeterminate(false);
        // 設定進度條
        dialog.incrementProgressBy(50);
        // 設定第二進度條
        dialog.incrementSecondaryProgressBy(75);
        dialog.show();
    }
}
```

#### 設定視窗不可被使用者關閉
```java
public class MainActivity extends Activity {
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        ProgressDialog dialog = new ProgressDialog(this);
        //關閉取消視窗功能
        dialog.setCancelable(false);
        dialog.show();
    }
}
```

#### 設定按鈕
```java
public class MainActivity extends Activity {
    private Activity activity;

    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        activity = this;

        ProgressDialog dialog = new ProgressDialog(this);
        dialog.setCancelable(false);
        dialog.setButton(DialogInterface.BUTTON_NEGATIVE, "確定", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int i) {
                Toast.makeText(activity, "關閉讀取視窗", Toast.LENGTH_SHORT).show();
            }
        });
        dialog.show();
    }
}
```

