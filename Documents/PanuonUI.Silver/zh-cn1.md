# PanuonUI.Silver中文手册  

***
# 目录
<!-- TOC --> 
- [使用指引](#使用指引)      
    - [STEP 1. 将Panuon.UI.Silver引入到你的项目中](#step-1-将panuonuisilver引入到你的项目中)
    - [STEP 2. 添加资源字典](#step-2-添加资源字典)
    - [STEP 3. 在代码中使用Panuon.UI.Silver](#step-3-在代码中使用panuonuisilver)
- [FontAwesome字体](#fontawesome字体)  
- [控件库](#控件库)      
    - [WindowX 窗体X](#windowx-窗体x)
<!-- TOC -->
***

## 使用指引  
  
### STEP 1. 将PanuonUI.Silver引入到你的项目中  
1. 以Nuget形式    
右击你的个人项目，选择“管理Nuget程序包”。在新打开的页面中，选择“浏览”，勾选“包括预发行版”选项，并在搜索框中输入“Panuon.UI.Silver”。选择最顶端的正确项目，并在右侧详情页中点击“安装”，等待安装完成即可。  
2. 以dll形式  
首先，打开资源管理器并定位到你项目的根文件夹中，右击创建一个名为“References”的文件夹。下载GitHub Zip文件并解压后，将解压文件夹目录下“Output/NET40”（若你的项目使用.NET4.5及以上框架，则为“Output/NET45”）文件夹内的所有dll文件拷贝到刚刚创建的References文件夹中。现在，切换到Visual Studio。在你项目下的“引用”条目上右击，并选择“添加引用”。点击右下角的“浏览”按钮，并导航到刚刚创建的References文件夹。全选这些dll文件，并点击“添加”，然后点击“确定”。
3. 以项目形式  
下载GitHub Zip文件并解压后，将解压文件夹目录下“Net40”（若你的项目使用.NET4.5及以上框架，则为“Net45”）文件夹内的“Panuon.UI.Silver”文件夹拷贝到你项目的根文件夹中。现在，切换到Visual Studio。右击你的解决方案，点击“添加” -> “现有项目”，定位到刚刚复制的Panuon.UI.Silver文件夹内，选择“Panuon.UI.Silver.csproj”，并点击确定。   

### STEP 2. 添加资源字典
打开你应用程序项目中的“App.xaml”，在&lt;Application.Resources&gt;节点内添加如下内容
```
<ResourceDictionary>
    <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="pack://application:,,,/Panuon.UI.Silver;component/Control.xaml" />
    </ResourceDictionary.MergedDictionaries>
</ResourceDictionary>
```
这将使Panuon.UI.Silver样式应用到整个程序。若你只希望在特定页面或控件中使用Panuon.UI.Silver样式，请将上述资源字典放置在特定页面的Resources节点内，而不是App.xaml中。  


### STEP 3. 在代码中使用PanuonUI.Silver
要在页面或控件中使用Panuon.UI.Silver，首先要在目标页面中添加命名空间引用。  
对于xaml代码，需要添加引用：  
```
xmlns:pu="clr-namespace:Panuon.UI.Silver;assembly=Panuon.UI.Silver"
```
以Window为例，添加pu命名空间引用后的Window如下：
```
<Window ...
        xmlns:pu="clr-namespace:Panuon.UI.Silver;assembly=Panuon.UI.Silver"
        ...>
    <Grid>
        <Button x:Name="BtnTest"
            pu:ButtonHelper.ButtonStyle="Link"
            pu:ButtonHelper.CornerRadius="15"
            Height="30"
            Width="150">
    </Gird>
</Window>
```
对于C#代码，需要添加引用：
```
using Panuon.UI.Silver;
```
若要对按钮实现上面xaml中的相同效果，则C#代码应如下：
```
ButtonHelper.SetButtonStyle(BtnTest, ButtonStyle.Link);
ButtonHelper.SetCornerRadius(BtnTest, 15);
```

## FontAwesome字体    
PanuonUI.Silver中集成了FontAwesome（v4.7）字体。你可以在你的项目中使用该字体：  

```
<TextBlock  FontFamily="{StaticResource FontAwesome}"
            Text="&#xf1b2;">
```  

Icon文字可以在 http://www.fontawesome.com.cn/cheatsheet/ 中查找。    

## 控件库

### WindowX 窗体X  

```
<pu:WindowX ...
            xmlns:pu="clr-namespace:Panuon.UI.Silver;assembly=Panuon.UI.Silver"
            pu:WindowXCaption.Height="35"
            pu:WindowXCaption.Foreground="Red">
</pu:WindowX>
```

WindowX使用原生的WindowChrome作为基础框架，因此不会引发AllowTransparent时的性能损失。如果默认的WindowX样式不能满足你的需要，你可以使用WindowXCaption辅助类来设计WindowX的窗体标题。  

WindowX中的自定义依赖属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
|IsMaskVisible | Boolean | False | 获取或设置窗体的遮罩层是否打开。|

WindowXCaption中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
Height | Double | 35.0 | 获取或设置标题栏的高度。
Background | Brush | Transparent | 获取或设置标题栏的背景色。
Foreground | Brush | #3E3E3E | 获取或设置标题栏的前景色。
Header | Object | Null | 获取或设置标题栏的内容。当此值不为Null时，Title和Icon将被隐藏，并显示为Header的内容。你可以通过此属性重新设计WindowX的标题栏。
ExtendControl | UIElement | Null | 获取或设置标题栏额外的控件，该控件将显示在最小化按钮的左侧。若要使用多个控件，你可以使用StackPanel或其他容器。
MinimizeButtonStyle | Style | - | 获取或设置最小化按钮的样式。
MaximizeButtonStyle | Style | - | 获取或设置最大化按钮的样式。
CloseButtonStyle | Style | - | 获取或设置关闭按钮的样式。
DisableCloseButton | Boolean | False | 获取或设置是否禁用关闭按钮。用户仍然可以通过强制关闭（例如Alt + F4）的方式关闭窗体。
HideBasicButtonsButton | Boolean | False | 获取或设置是否隐藏所有的基本按钮（最小化、最大化、关闭）。设置为True时，这些按钮的Visibility将设置为Collapsed。  


