# PanuonUI.Silver中文手册  

# 目录

- [欢迎使用](#欢迎使用)
- [使用指引](#使用指引)
    - [STEP 1. 将PanuonUI.Silver引入到你的项目中](#step-1-将panuonuisilver引入到你的项目中)
    - [STEP 2. 添加资源字典](#step-2-添加资源字典)
    - [STEP 3. 在代码中使用PanuonUI.Silver](#step-3-在代码中使用panuonuisilver)
- [FontAwesome字体](#fontawesome字体)
- [控件库](#控件库)
    - [WindowX 窗体X](#windowx-窗体x)
    - [Button 按钮 / RepeatButton 重复按钮](#button-按钮--repeatbutton-重复按钮)
    - [TextBox 文本输入框](#textbox-文本输入框)
    - [PasswordBox 密码输入框](#passwordbox-密码输入框)
    - [CheckBox 多选框](#checkbox-多选框)
    - [RadioButton 单选按钮](#radiobutton-单选按钮)
    - [ComboBox 单选框](#combobox-单选框)
    - [ProgressBar 进度条](#progressbar-进度条)
    - [TabControl 选项卡](#tabcontrol-选项卡)
    - [TreeView 树视图](#treeview-树视图)
    - [Slider 滑块](#slider-滑块)
    - [DataGrid 数据表](#datagrid-数据表)
    - [Loading 等待](#loading-等待)
    - [Menu 菜单](#menu-菜单)
    - [ContextMenu 上下文菜单](#contextmenu-上下文菜单)
    - [MessageBoxX 消息框](#messageboxx-消息框)
    - [PendingBox 等待框](#pendingbox-等待框)


***
## 欢迎使用

PanuonUI.Silver是一个可以高度自定义控件样式的Modern风格WPF控件库，其绝大多数控件都遵循了MVVM设计原则。PanuonUI.Silver的意义在于，你只需更改几个属性值，或调用一些方法，就可以轻松DIY出属于你自己风格的UI界面，而无需深入了解Style的写法，或是Trigger等属性的用法。  
PanuonUI.Silver不像DevExpress等控件库那样，通过简单的拖拖拽拽和点击，就能快速生成带有丰富色彩、统一风格的UI界面。虽然PanuonUI.Silver提供了一组默认的样式，但这些样式可能不能满足你的日常需求。UIBrowser中提供了“调色板”功能，你可以用它来快速设计、调整你的控件样式，并获取其代码。只需下载GitHub项目并用Visual Studio打开，你就能找到它。  
要最大化利用PanuonUI.Silver控件库的优势，你需要具有一定的审美能力，或者拥有一张现成的设计图。    

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
</pu:WindowX>
```
对于C#代码，需要添加引用：
```
using Panuon.UI.Silver;
```
若要对Button控件实现上面xaml中的相同效果，则C#代码应如下：
```
ButtonHelper.SetButtonStyle(BtnTest, ButtonStyle.Link);
ButtonHelper.SetCornerRadius(BtnTest, new CornerRadius(5));
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
| IsMaskVisible | Boolean | False | 获取或设置窗体的遮罩层是否打开。|
| MaskBrush | Brush | #AA3E3E3E | 获取或设置窗体遮罩层的颜色。|
| DisableForceClosing | Boolean | False | 获取或设置是否允许用户强制关闭窗体。若此值为True，用户只能通过关闭按钮来关闭窗体。若要在代码中执行关闭操作，必须使用ForceClose()方法。|

WindowX中的方法：  

| 方法名称 | 描述 | 参数 | 参数类型 | 参数描述 |
| - | - | - | - | - |
| ForceClose | 关闭当前窗体。当DisableForceClosing属性为True时，必须使用此方法关闭窗体。 | - | - | - |


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

***

### Button 按钮 / RepeatButton 重复按钮
代码示例：  
```
    <Button Height="30"
            Width="200"
            Content="Button"
            pu:ButtonHelper.ButtonStyle="Outline"
            pu:ButtonHelper.CornerRadius="15"/>
```
基础样式快照（与示例代码无关）：  

| 样式名称 | 静止 | 悬浮 |
| - | - | - |
| Standard | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/button-standard.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/button-standard-hover.png) |
| Hollow | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/button-hollow.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/button-hollow-hover.png) |
| Outline | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/button-outline.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/button-outline-hover.png) |
| Link | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/button-link.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/button-link-hover.png)  |

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

Tips :  
Q： 如何将一个Outline样式、圆角、点击时下沉的按钮样式应用到所有的控件？  
A: 添加以下样式：  
```
<Style TargetType="Button"
       BasedOn="{StaticResource {x:Type Button}}">
    <Setter Property="pu:ButtonHelper.ButtonStyle" 
            Value="Outline"/>
    <DataTrigger Binding="{Binding Path=(pu:ButtonHelper.ButtonStyle),RelativeSource={RelativeSource Self}, Mode=OneWay}"
                 Value="Outline">
        <Setter Property="pu:ButtonHelper.CornerRadius"
                Value="15"/>
        <Setter Property="pu:ButtonHelper.ClickStyle"
                Value="Sink"/>
    </DataTrigger>
</Style>
```
除了ButtonStyle外，其他的附加属性都应放在DataTrigger中。  

***

### TextBox 文本输入框
示例：  
```
    <TextBox Height="30"
             Width="200"
             pu:TextBoxHelper.Header="Account : "
             pu:TextBoxHelper.Watermark="PlaceHolder"
             pu:TextBoxHelper.CornerRadius="15"/>
```
基础样式快照（与示例代码无关）：  

| 静止 | 获得焦点 |
| - | - |
| ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/textbox.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/textbox-hover.png) |

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

Tips：  
Q: 如何禁用获得焦点时的外阴影效果？   
A: 将pu:TextBoxHelper.FocusedShadowColor设置为Null或{x:Null}即可。  

***

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
基础样式快照（与示例代码无关）：  

| 静止 | 获得焦点 |
| - | - |
| ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/passwordbox.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/passwordbox-hover.png) |

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

Tips：  
Q: 如何禁用获得焦点时的外阴影效果？   
A: 将pu:PasswordBoxHelper.FocusedShadowColor设置为Null或{x:Null}即可。  


***

### CheckBox 多选框
示例：  
```
    <CheckBox Height="30"
              Width="200"
              pu:CheckBoxHelper.Header="Available : "
              pu:CheckBoxHelper.CheckBoxStyle="Switch"/>
```

基础样式快照（与示例代码无关）：  

| 样式名称 | 静止 | 选中时 |
| - | - | - |
| Standard | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/checkbox-standard.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/checkbox-standard-checked.png) |
| Switch | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/checkbox-switch.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/checkbox-switch-checked.png) |
| Switch2 | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/checkbox-switch2.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/checkbox-switch2-checked.png) |
| Button | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/checkbox-button.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/checkbox-button-checked.png)  |

CheckBoxHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| CheckBoxStyle | CheckBoxStyle | Standard[/Switch/Switch2/Button] | 获取或设置多选框的基本样式。 |
| CheckedBackground | Brush | #3E3E3E[/#888888/#888888/-] | 获取或设置多选框被选中时的背景颜色。 |
| GlyphBrush | Brush | #FFFFFF | 获取或设置多选框的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| CheckedGlyphBrush | Brush | #FFFFFF | 获取或设置多选框被选中时的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| BoxHeight | Double | 16[/22/22/-] | 获取或设置多选框内的勾选框高度。在Button样式中，该属性无效。 |
| BoxWidth | Double | 16[/34/44/-] | 获取或设置多选框内的勾选框宽度。在Button样式中，该属性无效。 |
| CornerRadius | CornerRadius | 2,2,2,2 | 获取或设置密码框的圆角大小。在Switch样式中，该属性无效。 |
| CheckedContent | Object | Null | 获取或设置多选框被选中时的显示内容。若此值为Null，多选框在被选中时内容不会发生变化。 |
| NullGlyphBrush | Brush | #696969 | 获取或设置IsChecked为Null时符号的颜色。仅在Standard样式中生效，该值表示方形符号的颜色。请注意，IsChecked为Null时，也只有Standard样式会发生对应的变化。 |
| Header | Object | Null | 获取或设置显示在勾选框前的内容（通常是描述性文字）。该属性用于辅助用户快速生成一个 描述-多选框 的组合。 |
| HeaderWidth | String | "Auto" | 获取或设置Header的宽度。该属性支持GridLength的所有文本，例如"Auto"(自动)、‘"2*"(比例)、"50"(像素值)等。 |

***

### RadioButton 单选按钮
示例：  
```
    <RadioButton Height="30"
              Width="200"
              pu:RadioButtonHelper.Header="Option 1 : "
              pu:RadioButtonHelper.RadioButtonStyle="Switch"/>
```

基础样式快照（与示例代码无关）：  

| 样式名称 | 静止 | 选中时 |
| - | - | - |
| Standard | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/radiobutton-standard.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/radiobutton-standard-checked.png) |
| Switch | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/radiobutton-switch.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/radiobutton-switch-checked.png) |
| Switch2 | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/radiobutton-switch2.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/radiobutton-switch2-checked.png) |
| Button | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/radiobutton-button.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/radiobutton-button-checked.png)  |

RadioButtonHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| RadioButtonStyle | RadioButtonStyle | Standard[/Switch/Switch2/Button]] | 获取或设置单选按钮的基本样式。 |
| CheckedBackground | Brush | #3E3E3E[/#888888/#888888/-] | 获取或设置单选按钮被选中时的背景颜色。 |
| GlyphBrush | Brush | #FFFFFF | 获取或设置单选按钮的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| CheckedGlyphBrush | Brush | #FFFFFF | 获取或设置单选按钮被选中时的符号颜色。在Standard样式中，该值表示对勾的颜色。在Switch/Switch2样式中，该值表示圆形纽扣的颜色。在Button样式中，该属性无效。 |
| BoxHeight | Double | 16[/22/22/-] | 获取或设置单选按钮内的勾选框高度。在Button样式中，该属性无效。 |
| BoxWidth | Double | 16[/34/44/-] | 获取或设置单选按钮内的勾选框宽度。在Button样式中，该属性无效。 |
| CornerRadius | CornerRadius | 0,0,0,0 | 获取或设置密码框的圆角大小。在Switch样式中，该属性无效。 |
| CheckedContent | Object | Null | 获取或设置单选按钮被选中时的显示内容。若此值为Null，单选按钮在被选中时内容不会发生变化。 |
| NullGlyphBrush | Brush | #696969 | 获取或设置IsChecked为Null时符号的颜色。仅在Standard样式中生效，该值表示方形符号的颜色。请注意，IsChecked为Null时，也只有Standard样式会发生对应的变化。 |
| Header | Object | Null | 获取或设置显示在勾选框前的内容（通常是描述性文字）。该属性用于辅助用户快速生成一个 描述-单选按钮 的组合。 |
| HeaderWidth | String | "Auto" | 获取或设置Header的宽度。该属性支持GridLength的所有文本，例如"Auto"(自动)、‘"2*"(比例)、"50"(像素值)等。 |

***

### ComboBox 下拉单选框
示例：  
```
    <ComboBox Height="30"
              Width="200"
              pu:ComboBoxHelper.Header="Select one : "
              pu:ComboBoxHelper.ItemHeight="30"/>
```
基础样式快照（与示例代码无关）：  

| 静止 | 展开 |
| - | - |
| ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/comboxbox.png)  | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/comboxbox-expanded.png) |

ComboBoxHelper 中的附加属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| ItemHeight | Double |  | 获取或设置下拉单选框子项的统一高度。若要使用自动高度，请将值设置为NaN。 |
| HoverForeground | Brush |  | 获取或设置鼠标悬浮时下拉单选框子项的前景颜色。 |
| HoverBackground | Brush |  | 获取或设置鼠标悬浮时下拉单选框子项的背景颜色。 |
| SelectedForeground | Brush |  | 获取或设置下拉单选框子项被选中时的前景颜色。 |
| SelectedBackground | Brush |  | 获取或设置下拉单选框子项被选中时的背景颜色。 |
| CornerRadius | CornerRadius |  | 获取或设置下拉单选框的圆角大小。 |
| Icon | Object | Null | 获取或设置下拉单选框的Icon，该Icon将显示在Text之前。Icon可以是FontAwesome字体、图片Uri字符串或任何控件。 |
| Watermark | String | Null | 获取或设置下拉单选框的水印（PlaceHolder）。 |
| IsSearchTextBoxVisible | Boolean | False | 获取或设置是否在下拉单选框中显示搜索框。必须对SearchTextChanged事件添加处理，才能达到搜索效果。 |
| SearchTextBoxWatermark | String | "Search ..." | 获取或设置下拉单选框中搜索框的水印。 |

ComboBoxHelper 中的事件：  
| 事件名称 | 事件参数 | 事件描述 | 
| - | - | - |
| SearchTextChanged | SearchTextChangedEventHandler | 指示搜索框中的文字发生了变化。 |

Tips：  
Q: 在搜索框中输入了文字，但是没有搜索效果？   
A: PanuonUI不会自动执行搜索操作（因为在启用虚拟化场景下无法获取到下拉框的所有子项）。必须对SearchTextChanged添加处理方法，以控制子项的显隐。  

***

### ProgressBar 进度条
示例：  
```
    <ProgressBar Height="30"
              Width="200"
              pu:ProgressBarHelper.CornerRadius="15"
              pu:ProgressBarHelper.IsPercentVisible="True"/>
```
基础样式快照（与示例代码无关）：  

| 样式名称 | 静止 |
| - | - |
| Standard | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/progressbar-standard.png)  |
| Ring | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/progressbar-ring.png)  |

ProgressBarHelper 中的附加属性： 

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| ProgressBarStyle | ProgressBarStyle | Standard[/Ring]] | 获取或设置进度条的基本样式。 |
| CornerRadius | Double | 0 | 获取或设置进度条的圆角大小。在Ring样式中，该属性无效。 |
| AnimationTo | Double | 0 | 获取或设置进度条的动画目标值。此属性发生变化时，进度变化将使用动画效果。 |
| AnimationDuration | TimeSpan | 0:0:0.5 | 获取或设置当AnimateTo属性发生改变时，进度条动画效果的持续时间。 |
| IsPercentVisible | Boolean | False | 获取或设置是否显示百分比。在Standard样式中，文字会自动调整前景色，使其在任何进度下，数值都是可见的。 |

***

### TabControl 选项卡
示例：  
```
    <TabControl Height="30"
                Width="200"
                pu:TabControlHelper.ItemHeight="30"
                pu:TabControlHelper.CanRemove="True">
        <TabItem Header="Option1" />
        <TabItem Header="Option2" />
        <TabItem Header="Option3" />
    </TabControl>
```
基础样式快照（与示例代码无关）：  

| 样式名称 | 静止 |
| - | - |
| Standard | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/tabcontrol-standard.png)  |
| Classic | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/tabcontrol-classic.png) |
| Card | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/tabcontrol-card.png) |

TabControlHelper 中的附加属性： 

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| TabControlStyle | TabControlStyle | Standard[/Classic/Card]] | 获取或设置选项卡的基本样式。 |
| ItemHeight | Double | 40 | 获取或设置选项卡子项的统一高度。若要使用自动高度，请将值设置为NaN。 |
| SelectedForeground | Brush | 0 | 获取或设置选项卡被选中时的前景颜色。 |
| SelectedBackground | Brush | 0:0:0.5 | 获取或设置选项卡被选中时的背景颜色。 |
| ExtendControl | UIElement | Null | 获取或设置额外的控件，该控件将显示在选项卡列表的左侧。 |
| CanRemove | Boolean | False | 获取或设置是否允许移除选项卡。需要注意：对于使用ItemsSource属性绑定的方式，用户点击叉号后，该项目并不会从源数据集合中被移除，你需要对Removed事件进行额外处理。此属性既可以对TabControl控件生效，也可以对TabItem控件生效。 |
| ItemIcon | Object | Null | 获取或设置选项卡的Icon，该Icon将显示在Header之前。Icon可以是FontAwesome字体、图片Uri字符串或任何控件。此属性既可以对TabControl控件生效，也可以对TabItem控件生效。 |

TabControlHelper 中的事件：  
| 事件名称 | 事件参数 | 事件描述 | 
| - | - | - |
| Removed | TabItemRemovedEventArgs | 指示某个TabItem已经从视图中移除。 |

Tips：  
Q: 在使用ItemsSource生成数据时，为何点击删除按钮后，选项卡已从视图中移除，但数据仍存在于数据源集合中？   
A: 对于使用ItemsSource属性生成的选项卡集合，你需要对Removed事件进行额外处理，并将数据从数据源集合中删除。  

***

### TreeView 树视图
示例：  
```
    <TreeView Height="30"
                Width="200"
                pu:TreeViewHelper.ItemHeight="30"
                pu:TreeViewHelper.SelectMode="ChildOnly">
        <TreeViewItem Header="Header1" />
        <TreeViewItem Header="Header2" />
        <TreeViewItem Header="Header3" />
    </TreeView>
```
基础样式快照（与示例代码无关）：  

| 样式名称 | 静止 |
| - | - |
| Standard | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/treeview-standard.png)  |
| Classic | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/treeview-classic.png) |
| Modern | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/treeview-modern.png) |
| Chain | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/treeview-chain.png) |

TreeViewHelper 中的附加属性： 

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| TreeViewStyle | TreeViewStyle | Standard[/Classic/Modern/Card]] | 获取或设置树视图的基本样式。 |
| SelectMode | SelectMode | Any[/ChildOnly/Disabled] | 获取或设置树视图的选择模式。在ChildOnly模式下，只有没有子项（HasItems为False）的子项可以被选中。在Disabled模式下，任何子项都不能被选中。 |
| ExpandMode | ExpandMode | DoubleClick[/SingleClick] | 获取或设置树视图的展开/折叠模式。在SingleClick模式下，只需单击子项即可将其展开/折叠。 |
| ExpandBehaviour | ExpandBehaviour | Any[/OnlyOne] | 获取或设置树视图被的展开行为。在OnlyOne模式下，展开新子项时会将上一个展开的子项折叠（在深度大于2的树视图中可能会出现无法预料的结果）。 |
| ExpandedBrush | Brush | Null | 获取或设置树视图子项被展开时的背景色。仅对Classic和Modern样式生效。 |
| SelectedBackground | Brush | False | 获取或设置树视图子项被选中时的背景色。 |
| SelectedForeground | Brush | Null | 获取或设置树视图子项被选中时的前景色。 |
| ItemHeight | Double | 40 | 获取或设置树视图子项的统一高度。若要使用自动高度，请将值设置为NaN。 |
| ItemIcon | Object | 40 | 获取或设置树视图子项的Icon，该Icon将显示在Header之前。Icon可以是FontAwesome字体、图片Uri字符串或任何控件。此属性既可以对TabControl控件生效，也可以对TabItem控件生效。 |

***

### Slider 滑块
示例：  
```
    <Slider Height="30"
            Width="200"
            pu:SliderHelper.IsTickValueVisible="True" />
```
基础样式快照（与示例代码无关）：  

| 样式名称 | 静止 |
| - | - |
| Standard | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/slider-standard.png)  |
| Classic | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/slider-classic.png) |

DataTableHelper 中的附加属性： 

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| SliderStyle | SliderStyle | Standard[/Classic/] | 获取或设置滑块的基本样式。 |
| ThemeBrush | Brush |  | 获取或设置滑块已滑过区域的颜色。未滑过的区域颜色由Background属性控制。 |
| TrackThickness | Double | 3 | 获取或设置轨道的粗细。 |
| ThumbSize | Double | 16 | 获取或设置圆形纽扣的大小。 |
| IsTickValueVisible | Boolean | False | 获取或设置是否显示滑块的实时值。 | 

### DataGrid 数据表
示例：  
```
    <DataGrid ItemsSource="{Binding DataTable}"
              pu:DataGridrHelper.HeaderPadding="5,0"
              pu:DataGridrHelper.CellPadding="5,0" />
```
基础样式快照（与示例代码无关）：  
![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/datatable.png) 

DataGridHelper 中的附加属性： 

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| HeaderPadding | Thickness | 10,0,10,0 | 获取或设置数据表标题的内容间距。 |
| CellPadding | Thickness | 10,0,10,0 | 获取或设置数据表单元格的内容间距。 |
| HeaderMinHeight | Double |  | 获取或设置数据表标题的最小高度。 |
| RowMinHeight | Double |  | 获取或设置数据表行的最小高度。 |
| HeaderBackground | Brush |  | 获取或设置数据表标题的背景色。 |
| HeaderForeground | Brush |  | 获取或设置数据表标题的前景色。 |
| ResizeThumbThickness | Brush |  | 获取或设置数据表用于调整边距的滑块粗细。 |
| ResizeThumbBrush | Brush |  | 获取或设置数据表用于调整边距的滑块颜色。 |
| ColumnVerticalContentAlignment | VerticalAlignment | Center | 获取或设置数据表列内容位于垂直方向上的位置。 |
| ColumnHorizontalContentAlignment | HorizontalAlignment | Stretch | 获取或设置数据表列内容位于水平方向上的位置。 |
| HoverBackground | Brush |  | 获取或设置鼠标悬浮时数据表行或单元格的背景色。 |
| SelectedBackground | Brush |  | 获取或设置数据表行或单元格被选中时的背景色。 |
| SelectedForeground | Brush |  | 获取或设置数据表行或单元格被选中时的前景色。 |
| AutoGenerateCheckBoxStyle | Style | - | 获取或设置数据表自动生成的CheckBox的样式。 |
| RowHeaderBrush | Brush |  | 获取或设置数据表行标头的颜色。 |

与DataGrid有关的特性标签（Attribute）：  

| 特性标签 | 作用范围 | 描述 |
| - | - | - |
| IgnoreColumn | 属性 | 表示在数据表自动生成列时，应忽略该属性。 |
| ReadOnlyColumn | 属性 | 表示在数据表自动生成列时，应生成该属性的只读列。 |
| ColumnWidth | 属性 | 表示在数据表自动生成列时，应生成指定宽度的列。支持"auto"、"2*"、"100"等用法。 |

以上特性标签位于Panuon.UI.Silver.Core命名空间中。  

***

### Loading 等待

示例：  
```
    <pu:Loading Height="50"
                Width="50"
                LoadingStyle="Classic"
                IsRunning="True"/>
```

基础样式快照（与示例代码无关）：  

| 样式名称 | 静止 |
| - | - |
| Standard | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/loading-standard.png)  |
| Wave | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/loading-wave.png)  |
| Ring | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/loading-ring.png)  |
| Ring2 | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/loading-ring2.png)  |
| Classic | ![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/loading-classic.png)  |

Loading中的依赖属性：

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| LoadingStyle | LoadingStyle | Standard[/Wave/Ring/Ring2/Classic] | 获取或设置等待控件的基础样式。在Standard、Wave、Classic样式中，等待控件的颜色只受Foreground属性影响。在Ring、Ring2样式中，等待控件的颜色受Foreground、Background属性的影响。 |
| IsRunning | Boolean | False | 获取或设置等待控件是否正在运转。 |

***

### Menu 菜单

示例：  
```
    <Menu Height="50"
          Width="50">
        <MenuItem Header="Option1">
        <MenuItem Header="Option2">
    </Menu>
                 
```

基础样式快照（与示例代码无关）：  
![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/menu.png) 


MenuHelper中的附加属性：

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| MenuStyle | MenuStyle | Standard[/Modern] | 获取或设置菜单的基本样式。 |
| Orientation | Orientation | Horizontal | 获取或设置主菜单的布局方向。 |
| SubmenuCornerRadius | CornerRadius |  | 获取或设置子菜单的圆角大小。 |
| HoverBackground | Brush |  | 获取或设置鼠标悬浮时菜单子项的背景色。 |
| HoverForeground | Brush |  | 获取或设置鼠标悬浮时菜单子项的前景色。 |
| ShadowColor | Color? |  | 获取或设置菜单及子菜单的阴影颜色。若此值为Null，阴影效果将被禁用。 |
| SubmenuItemHeight | Double |  | 获取或设置菜单子项的统一高度。若要使用自动高度，请将值设置为NaN。 |
| ItemPadding | Thickness |  | 获取或设置菜单子项的统一内容间距。 |
| CheckableCheckboxStyle | Style | - | 获取或设置当菜单子项为Checkable时，替代Icon位置显示的CheckBox的样式。若此值为Null，子项被选中时Icon将被设置为一个对勾符号。 |

***

### ContextMenu 上下文菜单

示例：  
```
    <ContextMenu Height="50"
                 Width="50">
        <MenuItem Header="Option1">
        <MenuItem Header="Option2">
    </ContextMenu>
                
```

基础样式快照（与示例代码无关）：  
![](https://raw.githubusercontent.com/Panuon/Panuon.Documents/master/Resources/Panuon.UI.Silver/Snapshots/contextmenu.png) 


ContextMenuHelper中的附加属性：

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| CornerRadius | CornerRadius |  | 获取或设置上下文菜单及子菜单的圆角大小。 |
| HoverBackground | Brush |  | 获取或设置鼠标悬浮时上下文菜单子项的背景色。 |
| HoverForeground | Brush |  | 获取或设置鼠标悬浮时上下文菜单子项的前景色。 |
| ShadowColor | Color? |  | 获取或设置上下文菜单及子菜单的阴影颜色。若此值为Null，阴影效果将被禁用。 |
| ItemHeight | Double |  | 获取或设置上下文菜单子项的统一高度。若要使用自动高度，请将值设置为NaN。 |
| ItemPadding | Thickness |  | 获取或设置上下文菜单子项的统一内容间距。 |
| CheckableCheckboxStyle | Style | - | 获取或设置当上下文菜单子项为Checkable时，替代Icon位置显示的CheckBox的样式。若此值为Null，子项被选中时Icon将被设置为一个对勾符号。 |

***

### MessageBoxX 消息框

示例：  
```
var result = MessageBoxX.Show("This is a message.", "Tips", Application.Current.MainWindow);
```

MessageBoxX中的属性：

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| MessageBoxXConfigurations | IDictionary<string, MessageBoxXConfigurations> | - | 获取消息框的样式配置储存字典。 |

MessageBoxX中的方法：  

| 方法名称 | 描述 | 参数 | 参数类型 | 参数描述 |
| - | - | - | - | - |
| Show | 弹出一个消息对话框，并返回用户的选择结果（MessageBoxResult）。该方法有多个重载。 | message | String | 要显示的消息。 |
|  |  | title | String | 消息标题。 |
|  |  | owner | Window | 父窗体。 |
|  |  | messageBoxButton | MessageBoxButton | 要显示的按钮组。 |
|  |  | configKey | String | 预置的样式Key。 |
|  |  | configurations | MessageBoxXConfigurations | 指定的消息框样式配置。 |

MessageBoxXConfigurations中的属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| MessageBoxStyle | MessageBoxStyle | Standard[/Modern/Classic] | 设置消息框的基本样式。 |
| MessageBoxIcon | MessageBoxIcon | Info[/None/Success/Error/Warning] | 设置消息框的大图标样式。 |
| DefaultButton | DefaultButton | YesOK[/None/NoOrCancel/CancelOrNo] | 设置消息框的默认按钮。 |
| ButtonBrush | Brush | #55CEF1 | 设置消息框的主题颜色（按钮）。 |
| MinHeight | Double | 250 | 设置消息框的最小高度。 |
| MinWidth | Double | 500 | 设置消息框的最小宽度。 |
| MaxContentHeight | Double | 100 | 设置消息框的文本区域最大高度。超过此高度时，文本区域内将显示滚动条。 |
| MaxContentWidth | Double | 300 | 设置消息框的文本区域最大宽度。超过此宽度时，文本将自动换行。 |
| FontSize | Double | 16 | 设置消息框的文字大小。 |
| ShowInTaskbar | Boolean | True | 设置消息框窗体是否在任务栏中显示。 |
| Topmost | Boolean | True | 设置消息框是否显示在所有窗体的最顶端。 |
| WindowStartupLocation | WindowStartupLocation | CenterScreen[/Manual/CenterOwner] | 设置消息框的启动位置。 |
| InteractOwnerMask | Boolean | True | 设置消息框是否对父窗体的遮罩层产生交互（父窗体必须为WindowX类型）。若此值为True，消息框将在启动时显示父窗体的遮罩层，并在退出时关闭父窗体的遮罩层。 |
| YesButton | String | "Yes"("是 的") | 设置消息框“确定”按钮的内容文本。 |
| NoButton | String | "No"("不") | 设置消息框“否”按钮的内容文本。 |
| OKButton | String | "OK"("好 的") | 设置消息框“好的”按钮的内容文本。 |
| CancelButton | String | "Cancel"("取 消") | 设置消息框“取消”按钮的内容文本。 |
| ReverseButtonSequence | Boolean | False | 设置是否反转消息框的按钮顺序。 |

Tips：  
Q: MessageBoxXConfigurations属性和configKey参数该如何使用？   
A: MessageBoxXConfigurations属性提供了一个用于储存样式的字典。你可以在当前AppDomain内的任意位置向其中加入新样式，并在另一处代码中通过该样式的唯一key使用该样式。  

### PendingBox 等待框

示例：  
```
var handler = PendingBox.Show("Please wait ...", "Processing", false, Application.Current.MainWindow);
handler.UpdateMessage("Almost complete ...");
handler.Close();

//Cancelable
var handler = PendingBox.Show("Please wait ...", "Processing", true, Application.Current.MainWindow);
handler.Cancel += delegate
{
    //User Canceled
    handler.Close();
}
handler.UpdateMessage("Almost complete ...");
handler.Close();

```

PendingBox中的属性：

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| PendingBoxConfigurations | IDictionary<string, PendingBoxConfigurations> | - | 获取等待框的样式配置储存字典。 |

PendingBox中的方法：  

| 方法名称 | 描述 | 参数 | 参数类型 | 参数描述 |
| - | - | - | - | - |
| Show | 弹出一个无法被用户主动关闭的等待框，并返回一个控制器（IPendingHandler）。该方法有多个重载。 | message | String | 要显示的消息。 |
|  |  | title | String | 消息标题。 |
|  |  | cancelable | Boolean | 该等待框是否允许用户取消。用户点击取消按钮时会触发控制器的Cancel事件并禁用取消按钮，但窗体不会自动关闭。 |
|  |  | owner | Window | 父窗体。 |
|  |  | configKey | String | 预置的样式Key。 |
|  |  | configurations | PendingBoxConfigurations | 指定的等待框样式配置。 |

PendingBoxConfigurations中的属性：  

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
| PendingBoxStyle | PendingBoxStyle | Standard[/Classic] | 设置等待框的基本样式。 |
| LoadingStyle | LoadingStyle | Ring2[/Standard/Wave/Ring/Classic] | 设置等待框的等待控件样式。 |
| ButtonBrush | Brush | #55CEF1 | 设置等待框的按钮颜色。 |
| LoadingBackground | Brush | Transparent | 设置等待框的最小高度。 |
| LoadingForeground | Brush | #3E3E3E | 设置等待框的最小宽度。 |
| MaxContentHeight | Double | 100 | 设置等待框的文本区域最大高度。超过此高度时，文本区域内将显示滚动条。 |
| MaxContentWidth | Double | 300 | 设置等待框的文本区域最大宽度。超过此宽度时，文本将自动换行。 |
| FontSize | Double | 16 | 设置等待框的文字大小。 |
| ShowInTaskbar | Boolean | True | 设置等待框窗体是否在任务栏中显示。 |
| Topmost | Boolean | True | 设置等待框是否显示在所有窗体的最顶端。 |
| WindowStartupLocation | WindowStartupLocation | CenterScreen[/Manual/CenterOwner] | 设置等待框的启动位置。 |
| InteractOwnerMask | Boolean | True | 设置等待框是否对父窗体的遮罩层产生交互（父窗体必须为WindowX类型）。若此值为True，等待框将在启动时显示父窗体的遮罩层，并在退出时关闭父窗体的遮罩层。 |
| YesButton | String | "Yes"("是 的") | 设置等待框“确定”按钮的文本内容。 |
| NoButton | String | "No"("不") | 设置等待框“否”按钮的文本内容。 |
| OKButton | String | "OK"("好 的") | 设置等待框“好的”按钮的文本内容。 |
| CancelButton | String | "Cancel"("取 消") | 设置等待框“取消”按钮的文本内容。 |
| ReverseButtonSequence | Boolean | False | 设置是否反转等待框的按钮顺序。 |

Tips：  
Q: PendingBoxXConfigurations属性和configKey参数该如何使用？   
A: PendingBoxXConfigurations属性提供了一个用于储存样式的字典。你可以在当前AppDomain内的任意位置向其中加入新样式，并在另一处代码中通过该样式的唯一key使用该样式。  
