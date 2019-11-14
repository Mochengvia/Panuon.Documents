# Release Note

#### 2019-11-14 v1.0.9.3
[重要]Button / RepeatButton 的重大优化：  
解决了无法使用AccessKey的问题；解决了除Standard外的样式无法使用UI控件作为Content的问题；优化了悬浮效果，不会再与Foreground和BorderBrush重叠显示。  
删除了ClickHoverBrush属性，新增了ClickCoverOpacity属性，默认值为0.8。    

[重要]关于TreeView的问题修复：  
目前Standard样式下，子项选中的前景色是与SelectedBackground属性关联的。新版本中，已调整为SelectedForeground属性。  

#### 2019-11-13 v1.0.9.1 / v1.0.9.2
出于命名空间的重叠原因，TextBlock控件已重命名为PUTextBlock。  

## 2019-11-12 v1.0.9
修复ColorPicker点击控件外区域时不能自动关闭的问题，新增了HeaderWidth属性。  
修复ColorSelector的SelectedBrush赋值为null时崩溃的问题。  
修复了LayoutHelper的RowDefinition无效的问题。  
修复了WaterfallPanel中的控件设置高度无效的问题。  
为Slider控件新增了Header和HeaderWidth属性。  
新增了CheckBox和RadioButton的Selector样式。  
新增了TextBlock控件。MatchText和MatchedForeground属性可以用来高亮指定的文字，AutoAdaptation和ExceededTextFiller属性可以将超出显示边界的文本显示为省略号或其他文字。详见文档：  
https://github.com/Panuon/Panuon.Documents/blob/master/Documents/PanuonUI.Silver/zh-cn.md#textblock-%E6%96%87%E6%9C%AC%E6%8E%A7%E4%BB%B6
新增了AnimateWrapPanel控件，该控件继承自WrapPanel。当其Children发生变化时，将产生一个重新排列的动画效果。详见文档：  
https://github.com/Panuon/Panuon.Documents/blob/master/Documents/PanuonUI.Silver/zh-cn.md#animatewrappanel-%E5%8A%A8%E7%94%BB%E6%8D%A2%E8%A1%8C%E9%9D%A2%E6%9D%BF
Timeline控件重做，新增TimelineItem控件。该控件默认启用虚拟化。文档：  
https://github.com/Panuon/Panuon.Documents/blob/master/Documents/PanuonUI.Silver/zh-cn.md#timeline-%E6%97%B6%E9%97%B4%E8%BD%B4
移除了TagPanel控件，新增了TagControl和TagItem控件。该控件不支持虚拟化。文档：  
https://github.com/Panuon/Panuon.Documents/blob/master/Documents/PanuonUI.Silver/zh-cn.md#tagcontrol-%E6%A0%87%E7%AD%BE%E6%9D%BF

## 2019-11-6 v1.0.8.8
修复ComboBox的IsEditable属性设置为True时，Padding属性未对输入框生效的问题。  
修复ComboBox的BindToEnum属性在某些特定条件下可能报空指针异常，以及在使用BindToEnum属性时SelectedValue属性初始值无效的问题。  
新增了DataGridHelper中的SelectedItems属性。请注意，对该属性赋值是无效的。  

## 2019-11-1 v1.0.8.7
[严重]修复DataGrid在选中时前景色变灰的问题。    

## 2019-10-31 v1.0.8.6
修复WindowXCaption的Foreground属性未对标题和Header生效的问题。  
修复IconHelper.Width对除了Standard外的Button样式无效的问题。  
[重要]将CheckBox和RadioButton的CornerRadius属性由double类型调整为CornerRadius类型。  
修复ComboBox的SelectedForeground可能会显示异常的问题。  
移除了DataGridHelper多余的RowHeaderBrush属性。您可通过DataGrid的RowHeaderTemplate属性自由设置Header样式。同时，修复了DataGrid的Header没有显示的问题。  
修复了TabControlHelper.HeaderPanelBackground在TabStripPlacement不为Top时不生效的问题。  

## 2019-10-25 v1.0.8.5
修复了Calendar和DateTimePicker在选择月份时，若已选中了该月不存在的天数将引发崩溃的问题，以及无法处理SelectedDateTimeChanged事件的问题。新增了DateTimePicker的Header和HeaderWidth属性。  
修复了IconHelper.Width对TextBox不生效的问题。  
TabControl增强：  
新增ItemCornerRadius属性，用于设置选项卡子项的统一圆角大小。该属性也可直接对TabItem控件生效。  
新增ItemBackground属性，用于设置选项卡子项的统一背景色。  
新增HeaderPanelBackground属性，用于设置选项卡标题栏的背景色。   

Expander增强：  
移除了HeaderHeight属性，新增HeaderPadding（默认值5,5,0,5）、HeaderBackground、ShadowColor（默认值为Null）属性。  
调整默认Padding属性值为10,5。  

GroupBox增强：  
移除了Effect属性，新增Icon、HeaderPadding（默认值5,5,0,5）、HeaderBackground、ShadowColor（默认值为Null）属性。  
调整默认Padding属性值为10,5。  

## 2019-10-21 v1.0.8.4
修复了ScrollViewer.CanContentScroll在多个控件中不生效的问题。  
移除了GroupBox默认内部间距为0,3,0,3的设置。  
[严重]修复了ListBox样式没有应用到项目的问题。   

## 2019-10-16 v1.0.8.2/3
删除了MultiSelector控件。新增了MultiComboBox、MultiComboBoxItem控件。  
有关该控件的用法，请参考 https://github.com/Panuon/Panuon.Documents/blob/master/Documents/PanuonUI.Silver/zh-cn.md#multicombobox-%E4%B8%8B%E6%8B%89%E5%A4%9A%E9%80%89%E6%A1%86   
开放了ComboBoxHelper中的SearchText属性。  
新增了ColumnBindingAttribute，可使用此标记设置DataGrid自动生成列时的数据绑定方式。默认值调整为TwoWay、PropertyChanged。    

## 2019-10-15 v1.0.8.1
修复了TabControl在部分属性状态下显示异常的问题。  
新增了DisableScrollButton属性，通过该属性可以禁止两侧出现滚动按钮。  
移除了大多数控件中默认文字为微软雅黑UI的做法（便于Nuget用户更改字体）。  

## 2019-10-9 v1.0.7-rc
为了规范性和日后的发展，该版本改动较多，在更新之前请做好旧版本备份。  

新增了IconHelper辅助类，该类可以调整Button、TextBox、PasswordBox、ComboBox等带有Icon、ItemIcon属性的控件的图标字体、颜色、宽度及大小。  
ScrollViewerHelper中的ScrollBarCornerRadius和ScrollBarThickness属性现在可以对ListBox、TreeView等控件生效了。  
解除了所有控件中FocusVisualStyle为None的限制。   
将所有的ShadowColor属性由Color改为Color?类型。当其值为Null时，阴影效果将被禁用。  
优化了ColorPicker和ColorSelector的样式和效果。   
优化了DataGrid的验证错误样式，以及在SelectionUnit为Cell时的表现效果。  
新增了WaterfallPanel控件。  
新增了Menu样式，详见示例。  

WindowX :  
新增了DisableForceClosing属性。新增了ForceClose方法。  

WindowXCaption :  
新增了Padding属性。  

ComboBox :  
新增了SearchTextBoxWatermark属性。  
将SearchTextChanged事件的参数由RoutedPropertyChangedEventArgs<string>变更为SearchTextChangedEventArgs，该类型位于Panuon.UI.Silver.Core命名空间中。   

Loading :  
移除了Stroke和StrokeCover属性。在Standard、Wave、Classic样式中，Loading控件的颜色受Foreground属性影响。在Ring、Ring2样式中，Loading控件的颜色受Background、Foreground属性的影响。  

TextBox :  
新增了IsClearButtonVisible属性。  

PasswordBox :  
新增了IsShowPwdButtonVisible属性。  

TreeView :  
新增了ItemPadding属性。 
TreeViewItem的统一Padding值不再取自TreeView的Padding属性，而是由ItemPadding属性接管。  

TabControl :  
移除了不起作用的DisableSideButton属性，新增了ItemIcon、ItemPadding属性。  
TabItem的统一Padding值不再取自TabControl的Padding属性，而是由ItemPadding属性接管。  
将Removed事件的参数由RoutedPropertyChangedEventArgs<TabItem>>变更为TabItemRemovedEventArgs，该类型位于Panuon.UI.Silver.Core命名空间中。   

ContextMenu :  
移除了ItemIcon、ItemIconWidth属性。新增了CheckableCheckboxStyle属性。  

DateTimePicker :  
将SelectedDateTimeChanged事件的参数由RoutedPropertyChangedEventArgs<DateTime>变更为SelectedDateTimeChangedEventArgs，该类型位于Panuon.UI.Silver.Core命名空间中。  

WaterfallPanel & WaterfallViewer :  
新增了ChildrenShape、ChildrenShapeSizeDelta属性。  
通过ChildrenShape属性可以将Children中的元素设置成正方形。使用此属性后，可以使用ChildrenShapeSizeDelta属性对正方形元素的长/宽中的一个值（取决于Orienzation）进行增减。  

## 2019-9-10 v1.0.6  

1. 针对ComboBox的改动（`非常重要`）：  
将HoverBrush重命名为HoverBackground   
将SelectedBrush重命名为SelectedBackground  
新增了HoverForeground属性。  
新增了SelectedForeground属性。  

2. 针对ContextMenu的改动（`非常重要`）：  
将HoverBrush重命名为HoverBackground   
将SelectedBrush重命名为SelectedBackground  
新增了HoverForeground属性。    
新增了SelectedForeground属性。   
新增了ItemIconWidth属性，使用此属性可以调整ItemIcon的宽度。  
新增了ItemPadding属性，使用此属性可以统一设置Items的Padding。  

3. 针对ListBox的改动（`非常重要`）：  
将HoverBrush重命名为HoverBackground   
将SelectedBrush重命名为SelectedBackground  
新增了HoverForeground属性。  
新增了SelectedForeground属性。

4. 针对DropDown的改动：  
新增了IsAngleVisible属性，将此属性设置为False可隐藏顶部的尖角。   
新增了StaysOpen属性，将此属性设置为True可阻止DropDown自动关闭。   


## 2019-9-6 v1.0.5-rc  
1. 针对DataGrid的改动（`非常重要`）：  
移除了 'DataGridColumn' 特性。  
新增 'IgnoreColumn', 'ColumnWidth', 'ReadOnlyColumn' 特性。  
这些特性位于Panuon.UI.Silver.Core命名空间中。使用方式如下：  
```
[DisplayName("名称")]
[ColumnWidth("2*")]
[ReadOnlyColumn()]
public string Name { get;set; }

[IgnoreColumn()]
public object CustomData { get;set; }
```
新增了MouseEventHelper辅助类。  

