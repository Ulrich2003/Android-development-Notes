# 安卓线性布局LinearLayout
![在这里插入图片描述](https://img-blog.csdnimg.cn/dcc785067dbe4d46bc367f0b0162979c.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)
|属性|意义  |
|--|--|
| android:id | 定义id |
|android:layout_width  | 布局宽度（单位dp） |
| android:layout_height | 布局高度（单位dp） |
| android:background |布局背景  |
| android:layout_margin | 布局外边距（单位dp） |
|android:layout_padding  | 布局内边距（单位dp） |
| **android:orientation** | **定义布局方向** |
|**android:gravity**|**内部元素排放方式**|
|**android:layout_weight**|**权重（无单位）**|

#### android:gravity 示例代码

```xml
<LinearLayout
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:background="@color/black"
        android:gravity="center">
        <LinearLayout
            android:layout_width="50dp"
            android:layout_height="50dp"
            android:background="@color/white">
        </LinearLayout>
    </LinearLayout>
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/9435306badc043e09dec6c9b77f71f42.png)
#### android:layout_weight 简述
把「剩余」的宽度，或剩余的高度，按照「权重」去分配

```xml
 <LinearLayout
        android:layout_width="300dp"
        android:layout_height="300dp"
        android:background="@color/black">
        <View android:layout_height="match_parent"
            android:background="#2a9d8f"
            android:layout_width="0dp"
            android:layout_weight="2"/>
        <View android:layout_height="match_parent"
            android:background="#e9c46a"
            android:layout_width="0dp"
            android:layout_weight="1"/>
    </LinearLayout>
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/393ff5722b6a4c96a2e464e453ac9e57.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_9,color_FFFFFF,t_70,g_se,x_16)

