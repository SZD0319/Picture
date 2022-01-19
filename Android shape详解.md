### 用法

##### 创建文件

在 res/drawable 目录下新建一个 drawable resources file，它长这样：

```xml
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item>
        <shape>
            <solid></solid>
            <corners></corners>
            <gradient></gradient>
            <stroke></stroke>
        </shape>
    </item>
    <item>
        <shape></shape>		
    </item>
</selector>
```

根元素为 selector，表示选择器，在它之下可以创建多个 item，这些 item 主要作用是定义点放、选中、拖拽、激活、聚焦等状态。

##### 引用

可以在视图背景、字体颜色等属性中使用：

```xml
<TextView android:background="@drawable/btn_bg_selector"
          android:textColor="@drawable/btn_font_selector"></TextView>
```

------

### <shape> 下标签介绍

##### solid

指定内部填充色。

```xml
<solid  android:color="" />  
```

##### corners

定义圆角

```xml
<corners 
    android:radius="dimension"      
    android:topLeftRadius="dimension"   
    android:topRightRadius="dimension"    
    android:bottomLeftRadius="dimension" 
    android:bottomRightRadius="dimension" /> 
```

##### gradient

定义渐变色。

```xml
<gradient 
    android:type=["linear" | "radial" | "sweep"]    //共有3中渐变类型，线性渐变（默认）/放射渐变/扫描式渐变  
    android:angle="integer"     //渐变角度，必须为45的倍数，0为从左到右，90为从上到下，仅对线性有效  
    android:centerX="float"     //渐变中心X的相当位置，范围为0～1  
    android:centerY="float"     //渐变中心Y的相当位置，范围为0～1  
    android:startColor="color"   //渐变开始点的颜色  
    android:centerColor="color"  //渐变中间点的颜色，在开始与结束点之间  
    android:endColor="color"    //渐变结束点的颜色  
    android:gradientRadius="float"  //渐变的半径，只有当渐变类型为radial时才能使用  
    android:useLevel=["true" | "false"]  //使用LevelListDrawable时就要设置为true。设为false时才有渐变效果  
/>
```

##### stroke

定义边框。

```xml
<stroke       
    android:width="dimension"   //描边的宽度  
    android:color="color"   //描边的颜色  
    // 以下两个属性设置虚线  
    android:dashWidth="dimension"   //虚线的宽度，值为0时是实线  
    android:dashGap="dimension" />      //虚线的间隔 
```

------

### shape 属性

```xml
android:shape=["rectangle" | "oval" | "line" | "ring"]  
shape的形状，默认为矩形，可以设置为矩形（rectangle）、椭圆形(oval)、线性形状(line)、环形(ring)  

下面的属性只有在android:shape="ring时可用：  
android:innerRadius         尺寸，内环的半径。  
android:innerRadiusRatio    浮点型，以环的宽度比率来表示内环的半径，  
android:thickness           尺寸，环的厚度  
android:thicknessRatio      浮点型，以环的宽度比率来表示环的厚度，例如，如果android:thicknessRatio="2"，  
android:useLevel            boolean值，如果当做是LevelListDrawable使用时值为true，否则为false. 
```

------

### item 属性

定义组件所属状态。

```xml
<item
      android:state_pressed="" android:state_accelerated="" android:state_activated="" android:state_active="" android:state_checked="" ...
      ></item>
```

