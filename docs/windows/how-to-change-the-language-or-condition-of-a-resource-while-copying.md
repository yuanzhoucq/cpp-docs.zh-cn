---
title: "How to: Change the Language or Condition of a Resource While Copying | Microsoft Docs"
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
  - "vc.resvw.resource.changing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Language property"
  - "condition property of resource"
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Change the Language or Condition of a Resource While Copying
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在资源中进行复制时，你可以更改其语言属性和\/或条件属性。  
  
-   资源的语言仅标识资源的语言。  这由 [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) 使用以帮助识别要查找的资源。  （但是，每种不与文本相关的语言的资源可能存在差异，例如，可能仅适用于日语键盘的加速器或仅适用于中文本地化生成的位图，等等。）  
  
-   资源的条件是定义的符号，后者标识了使用资源的此特定副本的条件。  
  
 语言和资源的条件显示在工作区窗口中资源名称之后的括号内。  在此示例中名为 IDD\_AboutBox 的资源使用芬兰语作为其语言，而其条件是 XX33。  
  
```  
IDD_AboutBox (Finnish – XX33)  
```  
  
### 复制的现有资源并更改其语言或条件  
  
1.  在 .rc 文件中或在[资源视图](../windows/resource-view-window.md)窗口中，右键单击要复制的资源。  
  
2.  从快捷菜单选择**“插入副本”**。  
  
3.  在**“插入资源副本”**对话框中：  
  
    -   在**“语言”**列表框中选择语言。  
  
    -   在**“条件”**框中键入条件。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [How to: Copy Resources](../windows/how-to-copy-resources.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)