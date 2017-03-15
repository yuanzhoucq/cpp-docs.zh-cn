---
title: "Changing the Properties of Multiple Accelerator Keys | Microsoft Docs"
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
  - "keyboard shortcuts [C++], property changing"
  - "accelerator tables [C++], changing properties"
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Changing the Properties of Multiple Accelerator Keys
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 更改多个快捷键的属性  
  
1.  双击[资源视图](../windows/resource-view-window.md)中的快捷键对应表图标以打开此表。  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  单击每个键时按住 Ctrl 键以选择要更改的快捷键。  
  
3.  转到[“属性”窗口](../Topic/Properties%20Window.md)并键入希望所有选择的快捷键共享的值。  
  
    > [!NOTE]
    >  每个修饰符值都作为 Boolean 属性出现在“属性”窗口中。  如果在“属性”窗口中更改 [Modifier](../windows/accelerator-modifier-property.md) 值，快捷键对应表会将新修饰符视为对先前已存在的任何修饰符的附加。  因此，在设置任何修饰符值时，需要设置所有修饰符值以确保每个快捷键共享相同的 Modifier 设置。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Editing Accelerator Tables](../windows/editing-accelerator-tables.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)