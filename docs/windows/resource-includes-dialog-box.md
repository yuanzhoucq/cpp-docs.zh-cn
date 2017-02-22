---
title: "“资源包括”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.resourceincludes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“资源包括”对话框"
  - "rc 文件，更改存储区"
  - "符号头文件，更改"
  - "编译源代码，包含资源"
  - ".rc 文件，更改存储区"
  - "符号头文件，只读"
  - "符号，符号头文件"
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# “资源包括”对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用“资源包括”对话框，修改将所有资源存储在项目 .rc 文件中以及将所有[符号](../mfc/symbols-resource-identifiers.md)存储在 Resource.h 中的环境正常工作安排。  
  
 若要打开“资源包括”对话框，则右击[资源视图](../windows/resource-view-window.md)中的 .rc 文件，然后选择从快捷菜单中选择“资源包括”。  
  
 **符号头文件**  
 允许更改头文件的名称，头文件是存储资源文件的符号定义的位置。  有关详细信息，请参阅[更改符号头文件的名称](../windows/changing-the-names-of-symbol-header-files.md)。  
  
 **只读符号指令**  
 允许包含含有编辑会话期间不应修改的符号的头文件。  例如，可以包括在多个项目间共享的符号文件。  此外也可以包括 MFC.h 文件。  有关详细信息，请参阅[包括共享（只读）或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)。  
  
 **编译时指令**  
 允许包括所创建的资源文件，并可从主资源文件中的资源分别进行编辑，包含编译时指令（比如那些有条件地包括资源的指令），或者包含自定义格式的资源。  还可以使用“编译时指令”框包括标准 MFC 资源文件。  有关详细信息，请参阅[在编译时包括资源](../windows/how-to-include-resources-at-compile-time.md)。  
  
> [!NOTE]
>  这些文本框中的条目将由  `TEXTINCLUDE 1`、`TEXTINCLUDE 2` 和 `TEXTINCLUDE 3` 分表进行标记后显示在 .rc 文件中。  有关详细信息，请参阅[TN035：在 Visual C\+\+ 中使用多个资源文件和头文件](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。  
  
 一旦使用“资源包括”对话框更改了资源文件，你需要关闭 .rc 文件，然后重新打开它，以使更改生效。  有关详细信息，请参阅[在编译时包括资源](../windows/how-to-include-resources-at-compile-time.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [How to: Specify Include Directories for Resources](../windows/how-to-specify-include-directories-for-resources.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)