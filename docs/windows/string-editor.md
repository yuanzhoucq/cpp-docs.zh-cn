---
title: "String Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.string.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "String editor"
  - "string tables"
  - "string tables, String editor"
  - "string editing"
  - "string editing, string tables"
  - "resource editors, String editor"
  - "strings [C++], editing"
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# String Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

字符串表是 Windows 资源，其中包含应用程序的所有字符串的 ID、值和标题的列表。 例如，状态栏提示位于字符串表中。  
  
 开发应用程序时，可以具有多个字符串表 — 每种语言或条件使用一个。 但是，可执行模块只有一个字符串表。 如果将表放入不同 DLL 中，则正在运行的应用程序可以引用多个字符串表。  
  
 通过字符串表可以更加轻松地将应用程序本地化为不同语言。 如果所有字符串都处于字符串表中，则可以通过翻译字符串（和其他资源）来本地化应用程序，而无需更改源代码。 这通常比在源文件中手动查找和替换各种字符串更加理想。  
  
 使用字符串编辑器可以：  
  
-   [搜索一个或多个字符串](../mfc/finding-a-string.md)。  
  
-   快速向字符串表中[插入新条目](../mfc/adding-or-deleting-a-string.md)。  
  
-   [在资源文件之间移动字符串](../mfc/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [对 ID、值和标题属性使用就地编辑](../mfc/changing-the-properties-of-a-string.md)并立即查看更改。  
  
-   [更改多个字符串的标题属性](../mfc/changing-the-caption-property-of-multiple-strings.md)  
  
-   [为字符串添加格式设置或特殊字符](../mfc/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Windows 不允许创建空字符串表。 如果创建的字符串表中没有任何条目，则它在保存资源文件时会自动删除。  
  
 有关将资源添加到托管项目（以公共语言运行时为目标的项目）的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Resource Editors](../mfc/resource-editors.md)   
 [字符串](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [关于字符串](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)