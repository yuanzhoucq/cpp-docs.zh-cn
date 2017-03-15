---
title: "How to: Search for Symbols in Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbols, finding"
  - "resources [Visual Studio], searching for symbols"
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Search for Symbols in Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 在资源中查找符号  
  
1.  从“编辑”菜单选择“查找符号”。  
  
2.  在[“查找符号”对话框](http://msdn.microsoft.com/zh-cn/63e93d9c-784f-418d-a76a-723da5ff5d96)的“查找内容”框中，从下拉列表中选择以前的搜索字符串或键入要查找的加速键（例如 ID\_ACCEL1）。  
  
    > [!TIP]
    >  若要为搜索使用[正则表达式](../Topic/Using%20Regular%20Expressions%20in%20Visual%20Studio.md)，则必须使用“编辑”菜单中的[“在文件中查找”命令](../Topic/Find%20Command.md)，而不是“查找符号”命令。  若要启用正则表达式，则必须在[“查找”对话框](http://msdn.microsoft.com/zh-cn/dad03582-4931-4893-83ba-84b37f5b1600)中选中“使用：正则表达式”复选框。  然后，可单击“查找内容”框右侧的向右箭头按钮，以显示正则搜索表达式列表。  从此列表中选择表达式时，将使用“查找内容”框中的搜索文本来替换它。  
  
3.  选择任一“查找”选项。  
  
4.  单击“查找下一个”。  
  
    > [!NOTE]
    >  无法搜索字符串、快捷键或二进制资源中的符号。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)