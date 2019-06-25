# PanuonUI.Silver 中文手册

## 开始使用

1. 将"Panuon.UI.Silver.dll"添加到你项目的引用中。

2. 将以下资源字典添加到App.xaml、Window或其他UserControl的Resource中
```
<ResourceDictionary Source="pack://application:,,,/Panuon.UI.Silver;component/Control.xaml" />
```              

3. 在代码中添加引用。

```
(xaml)
xmlns:pu="clr-namespace:Panuon.UI.Silver;assembly=Panuon.UI.Silver"

(c#)
using Panuon.UI.Silver;
```

4. 开始使用：

在Xaml代码中：
```
<Button x:Name="BtnTest" 
        pu:ButtonHelper.ButtonStyle="Outline" />
```
或者，当你需要在C#代码中进行更改：
```
ButtonHelper.SetButtonStyle(BtnTest, ButtonStyle.Outline);
```

5. PanuonUI.Silver内部集成了FontAwesome字体文件（V4.6）。你可以在你的项目中使用它 :

```
FontFamily="{DynamicResource FontAwesome}"
```

从该链接中拷贝图标：http://www.fontawesome.com.cn/cheatsheet  



## Window 窗体
| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
Applying | Boolean | False | 获取或设置是否使用PanuonUI.Silver的窗体样式。
WindowAnimation | Enum(WindowAnimation) | None[/ Fade / Gradual / Scale] | 获取或设置窗体的启动/关闭动画。若要使用该属性，Applying属性的值必须为True。
OpenCoverMask | Boolean | False | 获取或设置窗体的遮罩层是否打开。若要使用该属性，Applying属性的值必须为True。
Icon | Object | Null | 获取或设置窗体标题左侧的Icon。它可以是FontAwesome字体，图片Uri字符串，或是任意控件。若要使用该属性，Applying属性的值必须为True。
NavbarBackground | Brush |  | 获取或设置窗体标题控制栏的背景色。
NavbarForeground | Brush |  | 获取或设置窗体标题控制栏的前景色。
NavbarHeight | Double |  | 获取或设置窗体标题控制栏的高度。将此属性的值设置为0，即可自定义你的窗体样式。
ExtendNavControl | UIElement | Null | 获取或设置窗体控制栏的额外控件。该控件将显示在窗体控制按钮（关闭、最大化、最小化）的左侧。若要添加多个控件，你可以使用StackPanel等容器。
DisableCloseButton | Boolean | False |获取或设置是否禁用窗体的关闭按钮。但用户仍然可以使用Alt + F4的方式强制关闭窗体。



|方法名称（参数） | 返回值 | 描述 |
| - | - | - |
ShowPopup(Window window, string content, double durationSeconds = 2) | void | 在窗体的下方弹出一个提示气泡。目标窗体的Applying属性无需为True，但目标窗体的Child控件必须为Grid。参数1：要弹出气泡的窗体。参数2：要显示的内容。参数3：气泡的持续时间（秒）。
ShowMessage(string content, string title = "Tips", Window owner = null, bool showInTaskbar = true, bool autoCoverMask = true) | void | 显示一个消息对话框。参数1：要显示的内容。参数2：窗体标题。参数3：对话框的父窗体，窗体将在父窗体的中央显示。参数4：是否在Taskbar中显示。参数5：是否在对话框弹出时打开Owner的遮罩层，并在对话框关闭时关闭Owner窗体的遮罩层。        
 ShowConfirm(string content, string title = "Tips", Window owner = null, bool showInTaskbar = true, bool autoCoverMask = true) | Boolean | 显示一个消息确认框。参数值同上。
ShowWaiting(Window owner, string content, string title = "Processing", Action cancelCallback = null, bool showInTaskbar = false, bool autoCoverMask = true) | void | 显示一个正在执行的消息框（以下简称该窗体为等待框），不应在一个窗体内同时显示多个等待框，这可能会引发未知的问题。参数1、2、3同上。参数4：用户点击取消按钮时的后续操作（等待框不会在用户点击取消按钮后自动关闭）；若该值为Null，取消按钮和关闭按钮将被禁用，但用户仍然可能通过其他手段强制关闭该窗体。参数5、6同上。
CloseWaiting(Window owner = null) | void | 关闭等待框。参数1：关闭指定父窗体的等待框。若此值为Null，则将关闭所有的等待框实例。若某个窗体中显示了多个等待框，可能会引发未知的问题。
        
# Button 按钮 / RepeatButton 重复按钮

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
ButtonStyle | Enum(ButtonStyle) | Standard[/ Hollow / Outline / Link] | 获取或设置按钮的基本样式。 
ClickStyle | Enum(ClickStyle) | None[/ Sink] | 获取或设置按钮点击时的样式。
HoverBrush | Brush | #3E3E3E | 获取或设置按钮悬浮时的遮罩颜色，该画刷将叠加在按钮的背景色或前景色上（取决于ButtonStyle）。
ClickCoverBrush | Brush | #22FFFFFF | 获取或设置按钮点击时的遮罩颜色，该画刷将叠加在按钮上。
CornerRadius | CornerRadius | 0 | 获取或设置按钮的边框圆角大小。
IsWaiting | Boolean | false | 获取或设置按钮是否处于等待状态。在等待状态下，按钮的Content将显示为一个Loading控件及WaitingContent的值，并且按钮将被禁用（透明度不会发生变化）。
WaitingContent | Object | Null | 获取或设置按钮处于等待状态时显示的内容。 
Icon | Object | Null | 获取或设置按钮的Icon。它可以是FontAwesome字体，图片Uri字符串，或是任意控件。请注意，Icon的颜色不受HoverBrush控制。

## TextBox 输入框

<TextBox pu:TextBoxHelper.Icon="/Resources/icon.png"
             pu:TextBoxHelper.Watermark="Put your text here">

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
Icon | Object | Null | 获取或设置输入框的Icon。它可以是FontAwesome字体，图片Uri字符串，或是任意控件。
Watermark | String | Null | 获取或设置输入框的水印。
CornerRadius | CornerRadius | 0 | 获取或设置输入框的边框圆角大小。
FocusedBorderBrush | Brush | Null | 获取或设置输入框获得焦点时的边框画刷。若其值为Null，输入框获得焦点时，边框画刷不会发生变化。
FocusedShadowColor | Color | #888888 | 获取或设置输入框获得焦点时的阴影颜色。

## PasswordBox 密码框
```
<PasswordBox pu:PasswordBoxHelper.Icon="/Resources/icon.png"
             pu:PasswordBoxHelper.Watermark="Put your password here"
             pu:PasswordBoxHelper.Password="{Binding Password, Mode=Twoway}">
```

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
Icon | Object | Null | 获取或设置密码框的Icon。它可以是FontAwesome字体，图片Uri字符串，或是任意控件。
Watermark | String | Null | 获取或设置密码框的水印。
CornerRadius | CornerRadius | 0 | 获取或设置密码框的边框圆角大小。
FocusedBorderBrush | Brush | Null | 获取或设置密码框获得焦点时的边框画刷。若其值为Null，密码框获得焦点时，边框画刷不会发生变化。
FocusedShadowColor | Color | #888888 | 获取或设置密码框获得焦点时的阴影颜色。
Password | String | Null | 获取或设置密码框的密码。密码框的Password属性不支持绑定，你可以在该属性上进行绑定（但这会使储存在计算机内存中的密码不再安全。若要彻底禁用该属性的功能，请在源代码中的Themes/PasswordBox.xaml中将PasswordHook属性设置为False(这是一个内部属性)）。

## CheckBox 复选框

术语注释：
1. 勾选框 ： 指复选框左侧，展示控件勾选状态的框体。


| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
CheckBoxStyle | Enum(CheckBoxStyle) | Standard[/ Switch / Button] | 获取或设置复选框的基本样式。
CheckedBackground | Brush |  | 获取或设置复选框被选中时的背景色（CheckBox的背景色仅控制勾选框的背景色）。
GlyphBrush | Brush | #FFFFFF | 获取或设置复选框的勾选框的前景色（Standard样式下对勾的颜色，Switch样式下Toggle圆球的颜色）
CheckedGlyphBrush | Brush | #FFFFFF | 获取或设置复选框被选中时，勾选框的前景色。
BoxHeight | Double | 16(Standard) / 22(Switch) | 获取或设置复选框的勾选框的高度。
BoxWidth | Double | 16(Standard) / 34(Switch) |获取或设置复选框的勾选框的宽度。
CorderRadius | CornerRadius | 0 | 获取或设置复选框的边框圆角大小（对Switch样式无效）。
CheckedContent | Object | Null | 获取或设置复选框被选中时替代Content显示的内容。若其值为Null，复选框被选中时，复选框的内容不会发生变化。

## RadioButton 单选框

术语注释：
1. 勾选框 ： 指单选框左侧，展示控件勾选状态的框体。

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
RadioButtonStyle | Enum(RadioButtonStyle) | Standard[/ Switch / Button] | 获取或设置单选框的基本样式。
CheckedBackground | Brush |  | 获取或设置单选框被选中时的背景色（CheckBox的背景色仅控制勾选框的背景色）。
GlyphBrush | Brush | #FFFFFF | 获取或设置单选框的勾选框的前景色（Standard样式下对勾的颜色，Switch样式下Toggle圆球的颜色）
CheckedGlyphBrush | Brush | #FFFFFF | 获取或设置单选框被选中时，勾选框的前景色。
BoxHeight | Double | 16(Standard) / 22(Switch) | 获取或设置单选框的勾选框的高度。
BoxWidth | Double | 16(Standard) / 34(Switch) |获取或设置单选框的勾选框的宽度。
CorderRadius | CornerRadius | 0 | 获取或设置单选框的边框圆角大小（对Switch样式无效）。
CheckedContent | Object | Null | 获取或设置单选框被选中时替代Content显示的内容。若其值为Null，单选框被选中时，单选框的内容不会发生变化。

## ComboBox 组合框

术语注释：
1. 子项 ： 该组合框中的ComboBoxItem（无论由Items还是ItemsSource生成）。

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
Icon | Object | Null | 获取或设置组合框的Icon。它可以是FontAwesome字体，图片Uri字符串，或是任意控件。
Watermark | String | Null | 获取或设置组合框的水印。
CorderRadius | CornerRadius | 0 | 获取或设置组合框的边框圆角大小。不宜设置为过大的值。
ItemHeight | Double | 30.0 | 获取或设置子项的默认高度。
HoverBrush | Brush | #EEEEEE | 获取或设置子项悬浮时的遮罩颜色，该画刷将叠加在子项的背景色上。
SelectedBrush | Brush | #DDDDDD | 获取或设置子项被选中时的遮罩颜色，该画刷将叠加在子项的背景色上。
ShadowColor | Color | #888888 | 获取或设置组合框的下拉框的阴影颜色。
IsSearchTextBoxVisible | Boolean | False | 获取或设置是否在组合框的下拉框中显示搜索框。你必须结合SearchTextChanged事件对用户输入的值进行手动处理（因为在启用虚拟化时，PanuonUI.Silver无法获取你所有的子项实例）。

| 事件名称 | 事件参数 | 描述 |
| - | - | - |
SearchTextChanged | String | 当用户在搜索框（IsSearchTextBoxVisible属性为True时显示）中输入内容时，触发此事件。事件的参数为String类型，参数内容为用户输入的值。在该事件的处理方法中，你可以通过将项目移除的方式来实现搜索，或是设置ComboBox的ItemContainerStyle属性，将ComboBoxItem的Visibility属性绑定到你的后台数据属性中。

## TreeView 树视图

术语注释：
1. 子项 ： 该树视图中的TreeViewItem（无论由Items还是ItemsSource生成）。


| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
TreeViewStyle | Enum(TreeViewStyle) | Standard[/ Classic / Modern / Chain] | 获取或设置树视图的基本样式。
SelectMode | Enum(SelectMode) | Any[/ ChildOnly] | 获取或设置树视图的选中模式。当属性值为ChildOnly时，所有含有子项（HasItems为True）的子项都无法被选中。
ExpandMode | Enum(ExpandMode) | DoubleClick[/ SingleClick] | 获取或设置树视图的展开模式。当属性值为SingleClick时，只需单击即可展开子项。
ExpandBehaviour | Enum(ExpandBehaviour) | Any[/ OnlyOne] | 获取或设置树试图的展开行为。当属性值为OnlyOne时，展开一个新的子项时将会折叠上一个子项（对于子项层级数大于2的树视图结构可能会出现问题）。
ItemHeight | Double | 40.0 | 获取或设置子项的默认高度。
SelectedBrush | Brush | #888888(Standard) / #DDDDDD | 获取或设置子项被选中时的遮罩颜色，该画刷将叠加在子项的背景色或前景色上（取决于TreeViewStyle）。
ExpandedBrush | Brush | #DDDDDD | 获取或设置子项展开时的遮罩颜色，该画刷将叠加在子项的背景色上（仅对Classic和Modern样式生效）。
ItemIcon | Object | Null | 获取或设置TreeViewItem的Icon。*该属性不是TreeView的有效属性，你需要将该属性应用于TreeViewItem对象上。*可以是FontAwesome字体，图片Uri字符串，或是任意控件。

## ProgressBar 进度条

| 属性名称 | 属性类型 | 默认值[其他值] | 描述 |
| - | - | - | - |
ProgressBarStyle | Enum(ProgressBarStyle) | Standard[/ Ring] | 获取或设置进度条的基本样式。
CorderRadius | CornerRadius | 0 | 获取或设置进度条的边框圆角大小。该属性对Ring样式无效。
AnimateTo | Double | 0 | 将进度条的Value值动态地变化到目标值。使用该属性可以获得动画增减的进度效果。
AnimationDuration | Timespan | 0:0:0.5 | 获取或设置AnimationTo属性进行动态变化的持续时间。
IsPercentVisible | Boolean | False | 获取或设置是否显示百分比进度。