---
title: "起始页体系结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "起始页体系结构"
  - "起始页 xaml"
ms.assetid: f94afe27-0be3-47d9-8e17-b0fd429017bd
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 起始页体系结构
本文档描述包含在 Visual Studio 起始页工具窗口的体系结构。  您可以使用此信息添加或更改在起始页的项，而不更改它的基础结构。  
  
 Visual Studio 起始页是 windows presentation foundation \(WPF\) 可扩展应用程序标记语言 \(xaml\)。  有关 XAML 标记的更多信息，请参见 [XAML 概述 \(WPF\)](../Topic/XAML%20Overview%20\(WPF\).md)。  
  
## 页框架  
 起始页包含一个 <xref:System.Windows.Controls.Image> 元素和两个 <xref:System.Windows.Controls.Grid> 元素在一个顶级 `Grid`元素。  `Image` 元素跨工具窗口的顶部和包含 Visual Studio 徽标。  在徽标下，左 `Grid`元素包含新项目的命令按钮， **最近访问项** 列表和启动 PAGE 选项的区域。  权限 `Grid`元素包含一个 **启动** 选项、一个 **指南和资源** 选项以及一个 **最新新闻** 选项的一个 <xref:System.Windows.Controls.TabControl> 元素。  中心列中定义的左右 `Grid`元素之间，但是，它没有内容并仅用作分隔。  
  
### windows 主体  
 工具窗口的背景是由顶级 `Grid`元素表示。  主列的宽度 \(以 `ColumnDefinitions` 元素中定义，这里。  徽标图像的高度 \(以 `RowDefinitions` 元素上设置。  
  
 定义行和列定义在从零开始的数组存储。  若要确定网格中的一个元素，请将 `Grid.Column` 和 `Grid.Row` 属性与相应的 <xref:System.Windows.Controls.ColumnDefinition> 和 <xref:System.Windows.Controls.RowDefinition> 元素的索引。  
  
### 徽标图像  
 Visual Studio 徽标占用顶部网格 \(`Grid.Row="0"`\) 的顶部行作为 `Image` 元素。  若要显示不同的图像，点 `Image` 元素的 `Source` 属性设置为一个不同的图像文件。  若要移除图像，请删除 `Image` 元素并将相应的顶部 `RowDefinition` 元素的 `height` 属性设置为 `0` \(0\) 隐藏网格的第一行。  
  
### 左列  
 起始页的左侧列由 `Grid.Column="0"` 和 `Grid.Row="1"`的一个 `Grid`元素表示。  此元素包含三行的定义，承载命令按钮网格、新项目网格和一个 `StackPanel` 元素显示 Visual Studio 选项。  
  
 可以将元素添加到该网格通过添加到一个现有的行或通过添加新的行定义。  在定义新行时，请确保将显示在新行下的所有元素的 `Grid.Row` 值。  
  
### 中间列  
 中间列是分隔并不包含元素。  若要将元素添加到中间列，请确保它在 `Grid.Column="1"` 和 `Grid.Row="1"`。  确保调整列定义的 `Width` 属性进行更改。  
  
### 正确的列  
 右列中包含一个 `Grid` 元素在 `Grid.Column="1"` 和 `Grid.Row="1"`。  网格包含三个选项卡的一个 `TabControl` 元素。  
  
 如 [演练: 将自定义 XAML 添加到开始页](../Topic/Walkthrough:%20Adding%20Custom%20XAML%20to%20the%20Start%20Page.md)所示，您可以通过将 <xref:System.Windows.Controls.TabItem> 元素添加到选项卡控件，，也可以编辑或移除现有的选项。  选项是从左到右在用户 \(UI\)界面中按与其显示为从上到下在标记中的顺序。  
  
 如果将元素添加到正确的列的网格在选项卡控件外部，建议您定义新行或列在网格确保显示按预期方式工作。  
  
## 请参阅  
 [自定义起始页](../Topic/Customizing%20the%20Start%20Page%20for%20Visual%20Studio.md)   
 [起始页最佳做法](../misc/start-page-best-practices.md)   
 [部署自定义起始页](../Topic/Deploying%20Custom%20Start%20Pages.md)