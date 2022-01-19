### Android 样式

样式是一个属性集合，用于指定单个 `View` 的外观。样式可以指定字体颜色、字号、背景颜色等属性。

##### 创建样式

在 res/values 目录下新建资源文件 styles.xml 文件，所有组件的样式都可以定义在里面。

styles.xml 文件的根标签是 <resources>，然后我们在根标签中定义 <style> 标签，一个 <style> 代表一个样式。

###### <style>

style 标签有两个属性：

- name：定义样式的名称，用于在 View 中引用
- parent：要继承的样式，一般是原组件的样式（xxx.AppCompat）

然后在 <style>  标签下添加 <item> 标签，一个 item 标签定义一个属性，比如字体、背景色等等。

###### <item>

item 标签需定义 name 属性，用于说明是样式的哪种属性。

我们来看一个例子：

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <style name="GreenText" parent="TextAppearance.AppCompat">
        <item name="android:textColor">#00FF00</item>
    </style>
</resources>
```

<br/>

##### 引用样式

在布局文件中添加如下内容：

```xml
<TextView
    style="@style/GreenText"
    ... />
```

<br/>

##### 应用场景

###### 自定义按钮

有时候我们想把各种 View 做成点击样式，就可以自己写一个 style，如下所示：

```xml
<style name="buttonStyle">
    <item name="android:textColor">@drawable/btn_font_selector</item>
    <item name="android:background">@drawable/btn_bg_selector</item>
    <item name="android:clickable">true</item>
    <item name="android:gravity">center</item>
</style>
```

**注意：**非 ButtonView 一定要加上属性 android:clickable="true"，否则点击样式不生效。

drawable/btn_font_selector.xml：

```xml
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_pressed="true" android:color="#FFF"/>
    <item android:state_pressed="false" android:color="@color/black"/>
</selector>
```

drawable/btn_bg_selector.xml：

```xml
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_pressed="true">
        <shape android:shape="rectangle">
            <solid android:color="@color/gray"/>
            <corners android:radius="4dp"/>
        </shape>
    </item>
    <item android:state_pressed="false">
        <shape android:shape="rectangle">
            <solid android:color="@color/teal_700"/>
            <corners android:radius="4dp"/>
        </shape>
    </item>
</selector>
```

如果想要点击时的**波纹效果**，只需在 <selector> 标签外层加上一个 <ripple> 标签。

```xml
<ripple android:color="@color/black" xmlns:android="http://schemas.android.com/apk/res/android">
    <item>
        <selector xmlns:android="http://schemas.android.com/apk/res/android">
            <item android:state_pressed="true">
                <shape android:shape="rectangle">
                    <solid android:color="@color/gray"/>
                    <corners android:radius="4dp"/>
                </shape>
            </item>
            <item android:state_pressed="false">
                <shape android:shape="rectangle">
                    <solid android:color="@color/teal_700"/>
                    <corners android:radius="4dp"/>
                </shape>
            </item>
        </selector>
    </item>
</ripple>
```

ripple 标签的 color 属性是必须的，表示波纹的的颜色。



### Android 主题

主题背景是应用于整个应用、Activity 或视图层次结构，而非仅仅应用于单个视图的属性集合。当您应用主题背景时，应用或 Activity 中的每个视图都会应用其支持的每个主题背景属性。主题还可以将样式应用于非视图元素，例如状态栏和窗口背景。