---
title: "扩展模式对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 扩展中的模式对话框"
  - "Visual Studio 扩展, 模式对话框"
ms.assetid: 478743dc-9fd9-46d7-9739-859fb8841a4f
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 扩展模式对话框
若要确保 Visual Studio 的功能和视觉兼容性，可通过从 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> 对象导出对话框窗口来为 Visual Studio 扩展创建模式对话框。 以这种方式导出的对话框还可以提供额外的功能，例如：可以设置 F1 帮助目标以及在窗口上实现最小化和最大化。  
  
## 创建模式对话框  
  
1.  在项目中，添加对 System.XAML 的引用。  
  
2.  在“解决方案资源管理器”中，右键单击项目，单击“添加”，然后单击“窗口”。  
  
3.  给窗口命名，然后单击“添加”。  
  
     此时设计器中会出现一个空的 XAML 窗口。  
  
4.  在顶级 `Window` 元素中，添加 <xref:Microsoft.VisualStudio.PlatformUI> 的命名空间声明，并将 `Window` 元素更改为 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> 元素，如下面的示例所示。  
  
     [!code-xml[VSModalDialog#02](../misc/codesnippet/Xaml/extending-modal-dialog-boxes_1.xaml)]  
  
5.  从“工具箱”中添加按钮、标签和其他控件，键入文本标签，并调整对话框的外观。  
  
6.  切换到代码视图。  
  
7.  在类定义中，将类设置为从 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 继承。 （默认情况下，类从 <xref:System.Windows.Window?displayProperty=fullName> 继承。）  
  
8.  为按钮和其他控件添加事件处理程序。  
  
#### 向模式对话框添加 F1 帮助  
  
1.  向构造函数添加一个使用字符串作为其实参的形参，并通过使用相同的形参将构造函数设置为从基构造函数继承，如下面的示例所示。  
  
     [!code-cs[VSModalDialog#12](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_2.cs)]  
  
     此构造函数将 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasHelpButton%2A> 属性设置为 `true`，并在用户按下 F1 键或单击“帮助”按钮时将接收到的字符串用作关键字。  
  
#### 向模式对话框添加“最小化”和“最大化”按钮  
  
1.  在构造函数中，将 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.hasMinimizeButton%2A> 和 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.hasHMaximizeButton%2A> 属性设置为 `true`，如以下下面的示例所示。  
  
     [!code-cs[VSModalDialog#13](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_3.cs)]  
  
    > [!WARNING]
    >  显示“最小化”和“最大化”按钮时，“帮助”按钮将处于隐藏状态，即使 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasHelpButton%2A> 属性设置为 `true` 也是如此。  
  
## 示例  
 下面的示例演示具有两个构造函数的模式对话框。 第一个构造函数采用 F1 关键字作为参数，并显示”帮助“按钮。 第二个构造函数不采用任何参数，但显示“最小化”和“最大化”按钮。 单击”是“按钮时，将调用该对话框的第二个实例，并启用“帮助”。  
  
 [!code-xml[VSModalDialog#01](../misc/codesnippet/Xaml/extending-modal-dialog-boxes_4.xaml)]  
  
 [!code-cs[VSModalDialog#11](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_5.cs)]  
  
 下面的代码从事件处理程序调用该对话框。  
  
 [!code-cs[VSModalDialog#21](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_6.cs)]  
  
## 请参阅  
 [创建和管理有模式对话框](../Topic/Creating%20and%20Managing%20Modal%20Dialog%20Boxes.md)