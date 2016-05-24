# TextView-EditText

android 40-43 lesson:
1.TextView:继承view组件,向用户显示文本，基本的配置为不允许编辑.如果要编辑用EditText,如果要允许用户复制TextView的值，设置XML属             性android:textSelectable为true或者在代码中用setTextIsSelectable(true)设置，标记TextView允许用户做出手势选择从而触             发内置的复制粘贴控制.
            
2.TextView实例：res->layout->activity_main.xml:
  <?xml version="1.0" encoding="utf-8"?>
  <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:tools="http://schemas.android.com/tools"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:paddingBottom="@dimen/activity_vertical_margin"
      android:paddingLeft="@dimen/activity_horizontal_margin"
      android:paddingRight="@dimen/activity_horizontal_margin"
      android:paddingTop="@dimen/activity_vertical_margin"
      tools:context="com.example.mackerlee.android_34.MainActivity">
  
      <TextView
        android:id="@+id/TextView01"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="TextView组件的使用"
        //--设置允许粘贴复制
        android:textIsSelectable="true"
        //--将drawable中的图片设置左边的背景图片
        android:drawableLeft="@drawable/mla"
        //--设置单行跑马灯方式显示过长文字
        android:ellipsize="marquee"
        android:singleLine="true"
        //--设置文本字体大小，用sp，宽高用dp
        android:textSize="30sp"
        //--设置文本样式风格，如粗体/斜体
        android:textStyle="bold/italic"/>
  </RelativeLayout>
  
  3.设置app->java->MainActivity.java:
    //--设置为对应的activity_main.xml
    setContentView(R.layout.activity_main); 
  4.TextView其他常用属性:
    --android:autoLink:设置下划线URL链接，即相当于网址可点击;
    --android:ellipsize:设置当文字过长时的显示方式，有以下值设置:start--省略号在开头，end--省略号在结尾，middle--省略号在中间,                     marquee--跑马灯方式显示，此时必须指定文本显示为一行.android:singleline="true".
    --android:textColor:设置文本颜色，采用RGB格式,如#00ff00
  
  5.EditText:是TextView的子类,所以TextView方法特性同样适用于EditText,但EditText用于编辑输入.
  6.EditText实例：res-layout-activity_main.xml
  <?xml version="1.0" encoding="utf-8"?>
  <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:tools="http://schemas.android.com/tools"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:paddingBottom="@dimen/activity_vertical_margin"
      android:paddingLeft="@dimen/activity_horizontal_margin"
      android:paddingRight="@dimen/activity_horizontal_margin"
      android:paddingTop="@dimen/activity_vertical_margin"
      tools:context="com.example.mackerlee.android_34.MainActivity">
  
      <TextView
          android:id="@+id/TextView02"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:text="TextView组件的使用"
          android:textIsSelectable="true"
          android:ellipsize="marquee"
          android:singleLine="true"
          android:drawableLeft="@drawable/mla"
          android:textSize="30sp"/>
  
      <EditText
          android:id="@+id/EditText01"
          android:layout_width="match_parent"
          android:layout_height="wrap_content"
          android:layout_below="@id/TextView02"
          //--设置输入类型,这样对应的键盘不一样，可以限制其他类型的输入，该属性可以并列设置几种方式,用|分割都在“”号中
          android:inputType="textPersonName"
          //--设置输入的最大长度
          android:maxLength="20"
          android:hint="请输入..."
          //--设置提示文字的颜色
          android:textColorHint="#238745"
          //--设置键盘出来后最后右下角的按钮是什么，此处设置为发送
          android:imeOptions="actionSend"/>
  
  </RelativeLayout>

7.EditText触发的事件，用于获取输入的值:app->java-包名->MainActivity.java:
            package com.example.mackerlee.android_34;
            
            import android.support.v7.app.AppCompatActivity;
            import android.os.Bundle;
            import android.view.KeyEvent;
            import android.view.inputmethod.EditorInfo;
            import android.widget.EditText;
            import android.widget.TextView;
            import android.widget.Toast;
            
            public class MainActivity extends AppCompatActivity {
            
                //--声明输入文本框
                private EditText editText01;
            
                @Override
                protected void onCreate(Bundle savedInstanceState) {
                    super.onCreate(savedInstanceState);
                    setContentView(R.layout.activity_main);
                    editText01 = (EditText)findViewById(R.id.EditText01);
                    //--为编辑框设置一个回车键监听事件处理，观察者模式
                    editText01.setOnEditorActionListener(new TextView.OnEditorActionListener(){
                        //--其中参数v就是当前editText01对象,actionId是activity_main.xml中设置的android:imeOptions值
                        public boolean onEditorAction(TextView v, int actionId, KeyEvent event){
                            //--判断actionId按钮的类型，从而进行事件处理
                            if(actionId== EditorInfo.IME_ACTION_SEND) {
                                String value = v.getText().toString();
                                Toast.makeText(MainActivity.this, value, Toast.LENGTH_LONG).show();
                            }
                            return false;
                        }
                    });
                }
            }
8.自定义actionID:在res->layout->activity_main.xml中定义android:imeActionLabel属性：
            <EditText
                    android:id="@+id/launch_codes"
                    android:layout_width="fill_parent"
                    android:layout_height="wrap_content"
                    android:hint="@string/enter_launch_codes"
                    android:layout_below="@id/EditText01"
                    android:inputType="number"
                    //--自定义 action button label，相当于自定义的android:imeOptions值
                    android:imeActionLabel="@string/launch" />
                    
