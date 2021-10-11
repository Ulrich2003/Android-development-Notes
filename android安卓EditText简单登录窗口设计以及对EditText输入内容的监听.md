# android安卓EditText简单登录窗口设计以及对EditText输入内容的监听
#### 成品示例
![在这里插入图片描述](https://img-blog.csdnimg.cn/adc1133ff55d47d79697acab5d1292c2.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)


#### layout文件代码📃

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".EditTextActivity"
    android:padding="15dp">

    <EditText
        android:id="@+id/et_1"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:textSize="16sp"
        android:textColor="#4b9ae9"
        android:hint="用户名"
        android:paddingLeft="10dp"
        android:background="@drawable/bg_username"
        android:textColorHint="#265cee"/>

    <EditText
        android:id="@+id/et_2"
        android:layout_below="@id/et_1"
        android:layout_marginTop="10dp"
        android:paddingLeft="10dp"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:textSize="16sp"
        android:textColor="#4b9ae9"
        android:background="@drawable/bg_username"
        android:hint="密码"
        android:inputType="textPassword"
        android:textColorHint="#265cee"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="70dp"
        android:layout_below="@+id/et_2"
        android:layout_marginTop="20dp"
        android:id="@+id/login_btn"
        android:background="@drawable/bg_btn4"
        android:text="登录"
        android:textColor="@color/white"
        android:textSize="25sp" />


</RelativeLayout>
```
#### drawable代码

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="#FFD3BB"/>
    <corners android:radius="20dp"/>
</shape>
```


![在这里插入图片描述](https://img-blog.csdnimg.cn/7cda91d87c90451f9e52401c3fb4fcf0.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAQ2h1YW5ZYW5nIENoZW4=,size_20,color_FFFFFF,t_70,g_se,x_16)
#### Activity代码：Toast效果，输入监听


```java
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.text.Editable;
import android.text.TextWatcher;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class EditTextActivity extends AppCompatActivity {
    private Button loginBtn;
    private EditText userName;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_edit_text);
        loginBtn = findViewById(R.id.login_btn);
        loginBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(EditTextActivity.this,"登录成功",Toast.LENGTH_SHORT).show();
            }
        });
        // 输入监听
        userName = findViewById(R.id.et_1);
        userName.addTextChangedListener(new TextWatcher() {
            @Override
            public void beforeTextChanged(CharSequence charSequence, int i, int i1, int i2) {

            }

            @Override
            public void onTextChanged(CharSequence charSequence, int i, int i1, int i2) {
                Log.d("Text Edit:",charSequence.toString());
            }

            @Override
            public void afterTextChanged(Editable editable) {

            }
        });
    }
}
```

## 代码中的输入监听板块
利用`addTextChangedListerner`监听输入框的变化

```java
// 输入监听
        userName = findViewById(R.id.et_1);
        userName.addTextChangedListener(new TextWatcher() {
            @Override
            public void beforeTextChanged(CharSequence charSequence, int i, int i1, int i2) {

            }

            @Override
            public void onTextChanged(CharSequence charSequence, int i, int i1, int i2) {
                Log.d("Text Edit:",charSequence.toString());
            }

            @Override
            public void afterTextChanged(Editable editable) {

            }
        });
```

