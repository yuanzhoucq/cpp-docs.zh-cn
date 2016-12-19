---
title: "Finding a String | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strings [C++], searching"
  - "strings [C++]"
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Finding a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以在字符串表中搜索一个或多个字符串，并将[正则表达式](../Topic/Using%20Regular%20Expressions%20in%20Visual%20Studio.md)用于“在文件中查找”命令（在“编辑”菜单中），以定位与某一模式匹配的所有字符串实例。  
  
### 在字符串表中查找字符串  
  
1.  双击[资源视图](../windows/resource-view-window.md)中的相应图标以打开字符串表。  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在“编辑”菜单上单击“查找和替换”，然后选择“查找”。  
  
3.  在**“查找内容”**框中，从下拉列表中选择上一个搜索字符串，或键入要查找的字符串的标题文本或资源标识符。  
  
4.  选择“查找”选项中的任何一个。  
  
5.  单击**“查找下一个”**。  
  
    > [!TIP]
    >  若要在搜索文件时使用正则表达式，请使用**“在文件中查找”**命令。  键入与某一模式匹配的正则表达式，或单击**“查找内容”**框右侧的按钮以显示正则搜索表达式列表。  当从该列表中选择某个表达式时，该表达式将替换**“查找内容”**框中的搜索文本。  如果使用正则表达式，请确保选定“使用: 正则表达式”复选框。  
  
 有关将资源添加到托管项目（面向公共语言运行时的那些项目）的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [String Editor](../mfc/string-editor.md)   
 [字符串](_win32_Strings)   
 [关于字符串](_win32_About_Strings_cpp)