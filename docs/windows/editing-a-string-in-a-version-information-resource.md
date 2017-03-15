---
title: "Editing a String in a Version Information Resource | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "version information resources"
  - "resources [Visual Studio], editing version information"
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Editing a String in a Version Information Resource
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 编辑版本信息资源中的字符串  
  
1.  单击相应项目一次以选择它，然后再次开始编辑它。 直接在版本信息表中或在[“属性”窗口](../Topic/Properties%20Window.md)中进行更改。 进行的更改会在这两个位置得到反映。  
  
     **注意** 在版本信息编辑器中编辑 **FILEFLAGS** 键时，你会注意到无法为 .rc 文件设置 **Debug**、**Private Build** 或 **Special Build** 属性（在“属性”窗口中）：  
  
    -   版本信息编辑器集会基于 **\_DEBUG** 生成标志，在资源脚本中使用 \#ifdef 设置 **Debug** 属性。  
  
    -   如果 **Private Build** 键在版本信息表中设置了 **Value**，则 **FILEFLAGS** 键的对应 **Private Build** 属性（在“属性”窗口中为 **True**。 如果 **Value** 为空，则该属性为 **False**。 同样，**Special Build** 键（在版本信息表中）会与 **FILEFLAGS** 键的 **Special Build** 属性关联。  
  
 可以通过单击键或值列标题来对字符串块的信息序列进行排序。 这些标题会自动将信息重新排列为所选顺序。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Version Information Editor](../mfc/version-information-editor.md)   
 [版本信息 \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)