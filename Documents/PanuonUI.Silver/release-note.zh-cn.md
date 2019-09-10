# Release Note  

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
