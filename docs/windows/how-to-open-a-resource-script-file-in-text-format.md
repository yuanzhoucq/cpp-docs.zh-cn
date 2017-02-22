---
title: "How to: Open a Resource Script File in Text Format | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.resource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource script files, opening in text format"
  - ".rc files, opening in text format"
  - "rc files, opening in text format"
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# How to: Open a Resource Script File in Text Format
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有时可能需要查看项目的资源脚本 \(.rc\) 文件的内容，而不在特定的资源编辑器中打开资源（如对话框）。  例如，可能需要在资源文件的所有对话框内搜索字符串，而不必分别打开每个对话框。  
  
> [!NOTE]
>  如果你的项目尚未包含 .rc 文件，请参阅[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
 可以以文本格式轻松打开资源文件，查看文件所包含的所有资源并执行[文本编辑器](http://msdn.microsoft.com/zh-cn/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)支持的全局操作。  
  
> [!NOTE]
>  资源编辑器不直接读取 .rc 或 resource.h 文件。  资源编译器将它们编译成由资源编辑器使用的 .aps 文件。  该文件是一个编译步骤，只存储符号数据。  与普通编译过程一样，非符号信息（如注释）在编译过程中将被放弃。   每当 .aps 文件与 .rc 文件不同步时，就会重新生成 .rc 文件（例如，当你进行“保存”时，资源编辑器将覆盖 .rc 文件和 resource.h 文件）。  对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。  有关如何保留注释的信息，请参阅[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。  
  
### 以文本格式打开资源脚本文件  
  
1.  从**“文件”**菜单中选择**“打开”**，然后单击**“文件”**。  
  
2.  在**“打开文件”**对话框中定位到要以文本格式查看的资源脚本文件。  
  
3.  突出显示该文件，然后单击**“打开”**按钮上的下拉箭头（位于按钮右边）。  
  
4.  从下拉菜单中选择**“打开方式”**。  
  
5.  在**“打开方式”**对话框中单击**“源代码\(文本\)编辑器”**。  
  
6.  从**“打开为”**下拉列表中选择**“文本”**。  
  
     资源在源代码编辑器中打开。  
  
 \- 或 \-  
  
1.  在**“解决方案资源管理器”**中右击 .rc 文件。  
  
2.  从快捷菜单中选择**“打开方式...”**，然后选择**“源代码\(文本\)编辑器”**。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)