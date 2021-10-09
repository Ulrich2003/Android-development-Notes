# Android安卓Button样式设置以及点击事件的绑定（案例篇）以及Button按钮背景色无效解决方法
新建一个🈳️的Activity，用于测试按钮 🔘
「不用好奇打马，只是为了让大家看的更清楚」
![在这里插入图片描述](https://img-blog.csdnimg.cn/fabbf72fb8194734a9a0e69a31df50fa.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)
### 几种按钮样式
#### 普通按钮：
```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="15dp">

    <!--普通按钮，有背景色，有字体颜色-->
    <Button
        android:id="@+id/btn_1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="#8b8497"
        android:text="按钮"
        android:textColor="#ec5f43"
        android:textSize="20dp" />
</RelativeLayout>
```
#### 从drawable获取到样式，而不是直接写background的按钮🔘：
```xml
......
<!--从drawable获取到样式，而不是直接写background-->
    <Button
        android:id="@+id/btn_2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/btn_1"
        android:layout_marginTop="10dp"
        android:background="@drawable/bg_btn2"
        android:text="ChuanyangChen"
        android:textColor="@color/white"
        android:textSize="20dp" />
......
```
drawable配置：
![在这里插入图片描述](https://img-blog.csdnimg.cn/5d24c10e63904763a04c32ee494f943a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">
    <solid android:color="#da6936"/>
    <corners android:radius="5dp"/>
</shape>
```
#### 只有边框，没有背景色的按钮，而且点击会弹出toast提醒⏰：

```xml
 <!--从drawable获取到样式，而不是直接写background-->
    <Button
        android:id="@+id/btn_3"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/btn_2"
        android:layout_marginTop="10dp"
        android:background="@drawable/bg_btn3"
        android:text="ChuanyangChen"
        android:textColor="#ec5f43"
        android:textSize="20dp" />
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/722e058f27bc43baa3a7e8065f5ad516.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">

    <stroke android:width="1dp" android:color="#3579c1"
        />
    <corners android:radius="15dp"/>
</shape>
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/83894bf7fb3a4cbcbf2f1f2ae49ff3c2.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)Toast提醒⏰JAVA实现：

```java
public class ButtonActivity extends AppCompatActivity {

    private Button mBtn3;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_button);
        mBtn3 = findViewById(R.id.btn_3);
        mBtn3.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(ButtonActivity.this,"按钮3被点击了",Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

#### 点击按钮会变色，并且弹出toast提醒⏰，不通过ID控制toast：
变色效果需要使用「selector」标签🏷️
![在这里插入图片描述](https://img-blog.csdnimg.cn/a1cb7504915449e1ae46d8c58726e7e6.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)

```xml
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_pressed="true">
        <shape>
            <solid android:color="#f7d05f"/>
            <corners android:radius="15dp"/>
        </shape>
    </item>
    <item android:state_pressed="false">
        <shape>
            <solid android:color="#ef8749"/>
            <corners android:radius="15dp"></corners>
        </shape>
    </item>
</selector>
```
Activity代码：拥有onClick属性的Button，不通过ID控制：
```xml
 <!--拥有onClick属性的Button，不通过ID控制-->
    <Button
        android:id="@+id/btn_4"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/btn_3"
        android:layout_marginTop="10dp"
        android:background="@drawable/bg_btn4"
        android:text="按压变色"
        android:onClick="showToast"
        android:textColor="@color/white"
        android:textSize="20dp" />
```

Java代码：

```java
public class ButtonActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        ......
    }
    public void showToast(View view){
        Toast.makeText(this,"按钮4被点击了",Toast.LENGTH_SHORT).show();
    }
}
```
# Button按钮background背景色无效解决方法
![在这里插入图片描述](https://img-blog.csdnimg.cn/193bd0e4747a4e07858c40a57aa2b4c8.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)

