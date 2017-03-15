---
title: "Version Information Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.version.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Version Information editor, about Version Information editor"
  - "editors, Version Information"
  - "resource editors, Version Information editor"
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Version Information Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

版本信息包括公司和产品标识、产品发行版号以及版权与商标通知。 使用版本信息编辑器，可以创建和维护存储在版本信息资源中的这些数据。 虽然应用程序不需要版本信息资源，但它是收集应用程序标识信息的有用位置。 安装 API 也使用版本信息。  
  
 版本信息资源有一个上部块和一个或多个下部块：顶部有一个固定信息块，底部有一个或多个版本信息块（适用于其他语言和\/或字符集）。 顶部块设有可编辑的数字框和可选择的下拉列表。 下部块仅包含可编辑的文本框。  
  
> [!NOTE]
>  Windows 标准是只具有一个名为 VS\_VERSION\_INFO 的版本资源。  
  
 使用“版本信息”编辑器，可以：  
  
-   [编辑版本信息资源中的字符串](../mfc/editing-a-string-in-a-version-information-resource.md)  
  
-   [添加其他语言的版本信息（新版本信息块）](../mfc/adding-version-information-for-another-language.md)  
  
-   [删除版本信息块](../mfc/deleting-a-version-information-block.md)  
  
-   [在程序内访问版本信息](../mfc/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  使用版本信息编辑器时，在许多情况下可以单击鼠标右键以显示资源命令的快捷菜单。 例如，如果你在指向块头条目时单击鼠标，快捷菜单将显示“新建版本块信息”和“删除版本块信息”命令。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Resource Editors](../mfc/resource-editors.md)   
 [菜单和其他资源](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)