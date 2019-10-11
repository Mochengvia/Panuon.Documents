# Release Note  

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

