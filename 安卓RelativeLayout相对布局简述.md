# 安卓RelativeLayout相对布局简述
![在这里插入图片描述](https://img-blog.csdnimg.cn/6b30f5316be045988c0e7925e6b683e1.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)
|属性|含义  |
|--|--|
|android:layout_toLeftOf  |  在谁的左边|
| android: layout_toRRightOf |在谁的右边  |
|android: layout_alignBottom  | 跟谁底部对齐 |
| android: layout_alignParentBottom |跟父空间底部对齐  |
| android: layout_below |  在谁的下边|

#### android: layout_toRRightOf 简述
```xml
<RelativeLayout android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:android="http://schemas.android.com/apk/res/android">
    <View
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:id="@+id/first"
        android:background="#fec5bb"></View>
    <View
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:background="#d8e2dc"
        android:layout_toRightOf="@id/first"></View>

</RelativeLayout>
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/55ceaa4afac24b038ae8d2e0a391fbf2.png)
#### android: layout_below 和 android: layout_alignBottom 区别
**android: layout_below：在谁的下边**

```xml
	<View
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:id="@+id/first"
        android:background="#fec5bb"></View>
    <View
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:background="#d8e2dc"
        android:layout_below="@id/first"></View>
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/dc6d5423532a4296ab0f8ad43a6f4e47.png)
**android: layout_alignBottom：跟谁底部对齐**

```xml
	<View
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:id="@+id/first"
        android:background="#fec5bb"></View>
    <View
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:background="#d8e2dc"
        android:layout_alignBottom="@id/first"></View>
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/7d83a8a36548441a97cc935b8f24d489.png)


