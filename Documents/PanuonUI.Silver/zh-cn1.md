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
## 欢迎使用

PanuonUI.Silver是一个可以高度自定义UI控件样式的Modern风格控件库，其绝大多数控件都遵循了MVVM设计原则。PanuonUI.Silver的意义在于，你只需更改几个属性值或调用一些方法，就可以轻松DIY出属于你自己风格的UI界面，而无需深入了解Style的写法，或是Trigger等属性的用法。因而采用PanuonUI.Sivler设计出的UI界面，风格可能是迥然不同的。  
PanuonUI.Silver不像DevExpress等控件库那样，通过简单的拖拖拽拽和点击，就能快速生成带有丰富色彩、且统一风格的UI界面。虽然PanuonUI.Silver提供了一组默认的样式，但这些样式可能不能满足你的日常需求，因此你可能需要借助UIBrowser中的“调色板”功能，来快速设计调整你的控件样式，并直接获取其代码。要最大化利用PanuonUI.Silver控件库的优势，你需要具有一定的审美能力，或是拥有一个出色的设计师小伙伴提供图纸。    

## 使用指引  
  
### STEP 1. 将PanuonUI.Silver引入到你的项目中  
1. 以Nuget形式    
右击你的个人项目，选择“管理Nuget程序包”。在包管理器页面中，点击“浏览”选项，然后在搜索框中键入“Panuon.UI.Silver”。选择最顶端的正确项目，并在右侧详情页中点击“安装”，等待安装完成即可。  
2. 以dll形式  
在你项目的根文件夹内创建一个名为“References”（当然其他的名字也可以）的文件夹。下载GitHub上的Zip文件并解压后，将解压文件夹目录下“Output/NET40”（若你的项目使用.NET4.5及以上框架，则为“Output/NET45”）文件夹内的所有dll文件拷贝到刚刚创建的文件夹中。切换到Visual Studio，在你项目下的“引用”条目上右击，并选择“添加引用”。点击右下角的“浏览”按钮，并导航到刚刚创建的References文件夹内。全选刚刚复制的dll文件，并点击“添加”按钮，然后再点击“确定”。
3. 以项目形式  
下载GitHub Zip文件并解压后，将解压文件夹目录下“Net40”（若你的项目使用.NET4.5及以上框架，则为“Net45”）文件夹内的“Panuon.UI.Silver”文件夹拷贝到你项目的根目录（或根目录内的子文件夹）中。切换到Visual Studio，右击你的解决方案，点击“添加” -> “现有项目”，定位到刚刚复制的Panuon.UI.Silver文件夹内，选择“Panuon.UI.Silver.csproj”，并点击“确定”按钮。  
在你要使用PanuonUI.Silver的项目下的“引用”条目上右击，并选择“添加引用”。选择“项目”选项卡，勾选“Panuon.UI.Silver”项目，并点击“确定”。   

### STEP 2. 添加资源字典
打开你应用程序项目中的“App.xaml”，在&lt;Application.Resources&gt;节点内添加如下内容
```
<ResourceDictionary>
    <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="pack://application:,,,/Panuon.UI.Silver;component/Control.xaml" />
    </ResourceDictionary.MergedDictionaries>
</ResourceDictionary>
```
这将使Panuon.UI.Silver样式应用到整个程序。若你只希望在特定页面或控件中使用Panuon.UI.Silver样式，请将上述资源字典放置在特定页面或控件的Resources节点内，而不是App.xaml中。  


### STEP 3. 在代码中使用PanuonUI.Silver
要在页面或控件中使用Panuon.UI.Silver，首先要在目标页面中添加命名空间引用。  
对于xaml代码，需要添加引用：  
```
xmlns:pu="clr-namespace:Panuon.UI.Silver;assembly=Panuon.UI.Silver"
```
以WindowX为例，添加pu命名空间引用后的WindowX如下：
```
<pu:WindowX ...
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
若要对Button控件实现上面xaml中的相同效果，则C#代码应如下：
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

Icon代码可以在 http://www.fontawesome.com.cn/cheatsheet/ 中查找和复制。    

## 控件库

### WindowX 窗体X  

示例：  
```
<pu:WindowX ...
            xmlns:pu="clr-namespace:Panuon.UI.Silver;assembly=Panuon.UI.Silver"
            pu:WindowXCaption.Height="35"
            pu:WindowXCaption.Foreground="Red">
</pu:WindowX>
```

WindowX使用原生WindowChrome作为框架，因此不会因为AllowTransparent而导致显著性能损失。如果默认的WindowX样式不能满足你的设计需求，你可以使用WindowXCaption辅助类来设计WindowX的标题。  

WindowX中的自定义依赖属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
|IsMaskVisible | Boolean | False | 获取或设置窗体的遮罩层是否打开。|
|DisableForceClosing | Boolean | False | 获取或设置是否允许用户强制关闭窗体。若此值为True，用户只能通过关闭按钮来关闭窗体。若要在代码中执行关闭操作，必须使用ForceClose()方法。|

WindowXCaption中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| Height | Double | 35.0 | 获取或设置标题栏的高度。 |
| Padding | Thickness | 0,0,0,0 | 获取或设置标题栏内容的边距。 |
| Background | Brush | Transparent | 获取或设置标题栏的背景色。 |
| Foreground | Brush | #3E3E3E | 获取或设置标题栏的前景色。 |
| Header | Object | Null | 获取或设置标题栏的内容。当此值不为Null时，Title和Icon将被隐藏，并显示为Header的内容。你可以通过此属性完全重设WindowX的标题栏。 |
| ExtendControl | UIElement | Null | 获取或设置标题栏额外的控件，该控件将显示在最小化按钮的左侧。若要使用多个控件，你可以使用StackPanel或其他容器。 |
| MinimizeButtonStyle | Style | - | 获取或设置最小化按钮的样式。 |
| MaximizeButtonStyle | Style | - | 获取或设置最大化按钮的样式。 |
| CloseButtonStyle | Style | - | 获取或设置关闭按钮的样式。 |
| DisableCloseButton | Boolean | False | 获取或设置是否禁用关闭按钮。若同时在WindowX中启用了DisableForceClosing属性，用户将只能通过管理员权限杀死进程的方式来强制关闭程序。 |
| HideBasicButtons | Boolean | False | 获取或设置是否隐藏所有的基本按钮（最小化、最大化、关闭）。设置为True时，这些按钮的Visibility将设置为Collapsed。 |  

Tips：  
Q: 如何完全隐藏窗体的标题栏？  
A: 将pu:WindowXCaption.Height设置为0即可。  

Q：为什么最小化按钮（/最大化按钮/关闭按钮）的样式不起作用？  
A：如果按钮的样式不是Standard，需要将所有的Setter放置在ButtonStyle的DataTrigger中。如果不明白，请参考UIBrowser/Resources/Styles.xaml中NeteaseMusicWindow样式的写法。  

### Button 按钮 / RepeatButton 重复按钮
示例：  
```
    <Button Height="30"
            Width="200"
            Content="Button"
            pu:ButtonHelper.ButtonStyle="Outline"
            pu:ButtonHelper.CornerRadius="15"/>
```

ButtonHelper  / RepeatButtonHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| ButtonStyle | ButtonStyle | Standard[/Outline/Hollow/Link] | 获取或设置按钮的基本样式。 |
| ClickStyle | ClickStyle | None[/Sink] | 获取或设置鼠标点击时按钮的样式。 |
| HoverBrush | Brush | #3E3E3E | 获取或设置鼠标悬浮时按钮的遮罩层。 |
| ClickCoverBrush | Brush | #22FFFFFF | 获取或设置鼠标点击时按钮的遮罩层。 |
| CornerRadius | CornerRadius | 0,0,0,0 | 获取或设置按钮的圆角大小。 |
| IsWaiting | Boolean | False | 获取或设置按钮是否处于等待模式。在等待模式时，按钮将处于禁用状态，并显示出一个Loading控件和WaitingContent的内容。 |
| WaitingContent | Object | "Please wait..." | 获取或设置按钮在IsWaiting为True时显示的内容。 |
| Icon | Object | Null | 获取或设置按钮的Icon，该Icon将显示在Content之前。Icon可以是FontAwesome字体、图片Uri字符串或任何控件。 |


### TextBox 文本输入框
示例：  
```
    <TextBox Height="30"
             Width="200"
             pu:TextBoxHelper.Header="Account : "
             pu:TextBoxHelper.Watermark="PlaceHolder"
             pu:TextBoxHelper.CornerRadius="15"/>
```

TextBoxHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| FocusedBorderBrush | Brush | Null | 获取或设置文本框获得焦点时的边框颜色。若此值为Null，文本框获得焦点时边框颜色不会发生任何变化。 |
| FocusedShadowColor | Color? | #888888 | 获取或设置文本框获得焦点时的阴影颜色。若此值为Null，文本框获得焦点时不会出现阴影。 |
| Watermark | Brush | Null | 获取或设置文本框的水印(PlaceHolder)。 |
| Icon | Object | Null | 获取或设置文本框的Icon，该Icon将显示在Text之前。Icon可以是FontAwesome字体、图片Uri字符串或任何控件。 |
| CornerRadius | CornerRadius | 0,0,0,0 | 获取或设置文本框的圆角大小。 |
| Header | Object | Null | 获取或设置显示在文本框前的内容（通常是描述性文字）。该属性用于辅助用户快速生成一个 描述-输入框 的组合。 |
| HeaderWidth | String | "Auto" | 获取或设置Header的宽度。该属性支持GridLength的所有文本，例如"Auto"(自动)、‘"2*"(比例)、"50"(像素值)等。 |
| IsClearButtonVisible | Boolean | False | 获取或设置是否显示清空按钮。 |


### PasswordBox 密码输入框
示例：  
```
    <PasswordBox Height="30"
                 Width="200"
                 pu:PasswordBoxHelper.Header="Password : "
                 pu:PasswordBoxHelper.Watermark="PlaceHolder"
                 pu:PasswordBoxHelper.CornerRadius="15"
                 pu:PasswordBoxHelper.Password="{Binding Password, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"/>
```

PasswordBoxHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| Password | String | Null | 获取或设置密码框的密码，该属性支持绑定。 |
| FocusedBorderBrush | Brush | Null | 获取或设置密码框获得焦点时的边框颜色。若此值为Null，密码框获得焦点时边框颜色不会发生任何变化。 |
| FocusedShadowColor | Color? | #888888 | 获取或设置密码框获得焦点时的阴影颜色。若此值为Null，密码框获得焦点时不会出现阴影。 |
| Watermark | Brush | Null | 获取或设置密码框的水印(PlaceHolder)。 |
| Icon | Object | Null | 获取或设置密码框的Icon，该Icon将显示在Text之前。Icon可以是FontAwesome字体、图片Uri字符串或任何控件。 |
| CornerRadius | CornerRadius | 0,0,0,0 | 获取或设置密码框的圆角大小。 |
| Header | Object | Null | 获取或设置显示在密码框前的内容（通常是描述性文字）。该属性用于辅助用户快速生成一个 描述-密码框 的组合。 |
| HeaderWidth | String | "Auto" | 获取或设置Header的宽度。该属性支持GridLength的所有文本，例如"Auto"(自动)、‘"2*"(比例)、"50"(像素值)等。 |
| IsShowPwdButtonVisible | Boolean | False | 获取或设置是否显示“显示密码”按钮。 |


### CheckBox 多选框
示例：  
```
    <CheckBox Height="30"
              Width="200"
              pu:CheckBoxHelper.Header="Available : "
              pu:CheckBoxHelper.CheckBoxStyle="Switch"/>
```

CheckBoxHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| CheckBoxStyle | CheckBoxStyle | Standard[/Switch/Switch2/Button]] | 获取或设置多选框的基本样式。 |
| CheckedBackground | Brush | Null | 获取或设置多选框被选中时的背景颜色。 |
| GlyphBrush | Brush | #888888 | 获取或设置多选框的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| CheckedGlyphBrush | Brush | Null | 获取或设置多选框被选中时的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| BoxHeight | Double | Null | 获取或设置多选框内的勾选框高度。在Button样式中，该属性无效。 |
| BoxWidth | Double | Null | 获取或设置多选框内的勾选框宽度。在Button样式中，该属性无效。 |
| CornerRadius | CornerRadius | 0,0,0,0 | 获取或设置密码框的圆角大小。在Switch样式中，该属性无效。 |
| CheckedContent | Object | Null | 获取或设置多选框被选中时的显示内容。若此值为Null，多选框在被选中时内容不会发生变化。 |
| NullGlyphBrush | Brush | "Auto" | 获取或设置IsChecked为Null时符号的颜色。仅在Standard样式中生效，该值表示方形符号的颜色。请注意，IsChecked为Null时，也只有Standard样式会发生对应的变化。 |
| Header | Object | Null | 获取或设置显示在勾选框前的内容（通常是描述性文字）。该属性用于辅助用户快速生成一个 描述-多选框 的组合。 |
| HeaderWidth | String | "Auto" | 获取或设置Header的宽度。该属性支持GridLength的所有文本，例如"Auto"(自动)、‘"2*"(比例)、"50"(像素值)等。 |

### RadioButton 单选按钮
示例：  
```
    <RadioButton Height="30"
              Width="200"
              pu:RadioButtonHelper.Header="Option 1 : "
              pu:RadioButtonHelper.RadioButtonStyle="Switch"/>
```

RadioButtonHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| RadioButtonStyle | RadioButtonStyle | Standard[/Switch/Switch2/Button]] | 获取或设置单选按钮的基本样式。 |
| CheckedBackground | Brush | Null | 获取或设置单选按钮被选中时的背景颜色。 |
| GlyphBrush | Brush | #888888 | 获取或设置单选按钮的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| CheckedGlyphBrush | Brush | Null | 获取或设置单选按钮被选中时的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| BoxHeight | Double | Null | 获取或设置单选按钮内的勾选框高度。在Button样式中，该属性无效。 |
| BoxWidth | Double | Null | 获取或设置单选按钮内的勾选框宽度。在Button样式中，该属性无效。 |
| CornerRadius | CornerRadius | 0,0,0,0 | 获取或设置密码框的圆角大小。在Switch样式中，该属性无效。 |
| CheckedContent | Object | Null | 获取或设置单选按钮被选中时的显示内容。若此值为Null，单选按钮在被选中时内容不会发生变化。 |
| NullGlyphBrush | Brush | "Auto" | 获取或设置IsChecked为Null时符号的颜色。仅在Standard样式中生效，该值表示方形符号的颜色。请注意，IsChecked为Null时，也只有Standard样式会发生对应的变化。 |
| Header | Object | Null | 获取或设置显示在勾选框前的内容（通常是描述性文字）。该属性用于辅助用户快速生成一个 描述-单选按钮 的组合。 |
| HeaderWidth | String | "Auto" | 获取或设置Header的宽度。该属性支持GridLength的所有文本，例如"Auto"(自动)、‘"2*"(比例)、"50"(像素值)等。 |

### ComboBox 单选框
示例：  
```
    <ComboBox Height="30"
              Width="200"
              pu:ComboBoxHelper.Header="Select one : "
              pu:ComboBoxHelper.ItemHeight="30"/>
```

ComboBoxHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| RadioButtonStyle | RadioButtonStyle | Standard[/Switch/Switch2/Button]] | 获取或设置单选按钮的基本样式。 |
| CheckedBackground | Brush | Null | 获取或设置单选按钮被选中时的背景颜色。 |
| GlyphBrush | Brush | #888888 | 获取或设置单选按钮的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| CheckedGlyphBrush | Brush | Null | 获取或设置单选按钮被选中时的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| BoxHeight | Double | Null | 获取或设置单选按钮内的勾选框高度。在Button样式中，该属性无效。 |
| BoxWidth | Double | Null | 获取或设置单选按钮内的勾选框宽度。在Button样式中，该属性无效。 |
| CornerRadius | CornerRadius | 0,0,0,0 | 获取或设置密码框的圆角大小。在Switch样式中，该属性无效。 |
| CheckedContent | Object | Null | 获取或设置单选按钮被选中时的显示内容。若此值为Null，单选按钮在被选中时内容不会发生变化。 |
| NullGlyphBrush | Brush | "Auto" | 获取或设置IsChecked为Null时符号的颜色。仅在Standard样式中生效，该值表示方形符号的颜色。请注意，IsChecked为Null时，也只有Standard样式会发生对应的变化。 |
| Header | Object | Null | 获取或设置显示在勾选框前的内容（通常是描述性文字）。该属性用于辅助用户快速生成一个 描述-单选按钮 的组合。 |
| HeaderWidth | String | "Auto" | 获取或设置Header的宽度。该属性支持GridLength的所有文本，例如"Auto"(自动)、‘"2*"(比例)、"50"(像素值)等。 |