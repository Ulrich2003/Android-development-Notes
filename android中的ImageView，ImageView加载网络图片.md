# android中的ImageView，ImageView加载网路图片
![在这里插入图片描述](https://img-blog.csdnimg.cn/b24318d8a0634225bbc31d84322c8a58.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)
#### 在布局文件中加入<ImageView>标签🏷️

```xml
<ImageView
        android:layout_width="300dp"
        android:layout_height="200dp"
        android:background="#111111"
        android:id="@+id/imageView_pic1"
        android:scaleType="fitXY"/>
```

#### ImageView加载网路图片
导入Glide图片加载框架
[GitHub地址：https://github.com/bumptech/glide/](https://github.com/bumptech/glide/)
添加Gradle依赖到项目中
![在这里插入图片描述](https://img-blog.csdnimg.cn/c530ec35bcc948d49df049c8446d4799.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)
在Activity对应的java文件中，使用Glide加载网络图片

```java
public class ImageViewActivity extends AppCompatActivity {

    private ImageView imageView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_image_view);
        imageView = findViewById(R.id.imageView_pic1);
        // 加载网络图片
        Glide.with(this).load("https://images.unsplash.com/photo-1609225151006-1d67f4e88db0?ixid=MnwxMjA3fDB8MHxwcm9maWxlLWxpa2VkfDZ8fHxlbnwwfHx8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=900&q=60").into(imageView);
    }
}
```
最终效果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/df883847337543dc99bd05843196a2c0.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)

