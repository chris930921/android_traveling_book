
```java
    private Activity activity;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        this.activity = this;

        final String[] content = {
                "直到我膝蓋中了一箭",
                "我本來不想用這招的",
                "眼鏡才是本體",
                "你們聊，我先走了",
                "你不是還有生命嗎?",
                "你有沒有感覺到我的...",
                "你為什麼不問問神奇海螺呢？",
                "哥哥你好英俊",
                "外國人都是很NICE的，這其中一定有什麼誤會",
                "女俠饒命呀！",
                "師父，救我啊!",
                "從此君王不早朝",
                "德國的科學力是世界第一",
                "我佛你",
                "我現在的心情你怎麼可能瞭解",
                "我要寫個慘字",
                "換個髮型就是新人物了",
                "時代的眼淚",
                "有奇怪的東西混進去了",
                "沒圖沒真相"
        };
        ViewGroup.LayoutParams params = new ViewGroup.LayoutParams(
                ViewGroup.LayoutParams.MATCH_PARENT,
                ViewGroup.LayoutParams.MATCH_PARENT);

        LinearLayoutManager linearManager = new LinearLayoutManager(this);
        linearManager.setOrientation(LinearLayoutManager.HORIZONTAL);  //水平

        DefaultItemAnimator animator = new DefaultItemAnimator();

        RecyclerView.Adapter adapter = new RecyclerView.Adapter() {
            @Override
            public RecyclerView.ViewHolder onCreateViewHolder(ViewGroup viewGroup, int i) {
                Button v = new Button(activity);
                RecyclerView.ViewHolder viewHolder = new RecyclerView.ViewHolder(v) {
                };
                return viewHolder;
            }

            @Override
            public void onBindViewHolder(RecyclerView.ViewHolder viewHolder, int i) {
                Button v = (Button) viewHolder.itemView;
                v.setText(content[i]);
            }

            @Override
            public int getItemCount() {
                return 20;
            }
        };

        RecyclerView v = new RecyclerView(this);
        v.setLayoutParams(params);
        v.setLayoutManager(linearManager);
        v.setItemAnimator(animator);
        v.setAdapter(adapter);

        setContentView(v);
    }
```

![](picture/02.png)
