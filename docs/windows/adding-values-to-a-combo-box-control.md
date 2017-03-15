---
title: "Adding Values to a Combo Box Control | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog.combo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "combo boxes [C++], Data property"
  - "controls [Visual Studio], testing values in combo boxes"
  - "combo boxes [C++], adding values"
  - "combo boxes [C++], previewing values"
  - "controls [C++], testing values in combo boxes"
  - "Data property"
  - "combo boxes [C++], testing values"
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Adding Values to a Combo Box Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

只要对话框编辑器是打开的，就可以向组合框控件添加值。  
  
> [!TIP]
>  最好在调整对话框编辑器中的组合框大小之前将所有的值添加到该框中，否则可能会截断应显示在组合框控件中的文本。  
  
#### 将值输入到组合框控件  
  
1.  单击组合框控件以选定它。  
  
2.  在[“属性”窗口](../Topic/Properties%20Window.md)中，向下滚动到 **Data** 属性。  
  
    > [!NOTE]
    >  如果正在显示按类型分组的属性，**Data** 将出现在**“杂项”**属性中。  
  
3.  在 **Data** 属性的值域中单击并键入以分号分隔的数据值。  
  
    > [!NOTE]
    >  不要在值之间插入空格，原因是空格会妨碍下拉列表中的字母排序。  
  
4.  完成添加值的操作后，单击“输入”。  
  
 有关扩大组合框下拉部分的信息，请参见[设置组合框及其下拉列表的大小](../mfc/setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。  
  
> [!NOTE]
>  不能使用此过程将值添加到 Win32 项目中（Win32 项目的 **Data** 属性是灰显的）。  由于 Win32 项目没有添加此功能的库，对于 Win32 项目必须以编程方式将值添加到组合框。  
  
#### 测试组合框中值的外观  
  
1.  在 **Data** 属性中输入值后，单击[“对话框编辑器”工具栏](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)上的“测试”按钮。  
  
     尝试在整个值列表中向下滚动。  显示的值与在“属性”窗口的 **Data** 属性中键入的值完全相同。  没有拼写或大小写检查。  
  
     按 Esc 返回到对话框编辑器。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 Win32  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)