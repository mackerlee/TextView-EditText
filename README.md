# TextView-EditText

android 40-41 lesson:
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
          //--设置输入类型,这样对应的键盘不一样，可以限制其他类型的输入，该属性可以并列设置几种方式
          android:inputType="textPersonName"
          android:hint="请输入..."
          //--设置键盘出来后最后右下角的按钮是什么，此处设置为发送
          android:imeOptions="actionSend"/>
  
  </RelativeLayout>
