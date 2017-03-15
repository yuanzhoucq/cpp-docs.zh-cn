---
title: "Accelerator Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.accelerator.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator tables [C++], editing"
  - "tables [Visual Studio], accelerator key"
  - "accelerator keys"
  - "resource editors, Accelerator editor"
  - "keyboard shortcuts [C++], Accelerator editor"
  - "Accelerator editor"
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Accelerator Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

快捷键对应表是一个 Windows 资源，包含由快捷键和与之关联的命令标识符组成的列表。 一个程序可以拥有多个快捷键对应表。  
  
 通常情况下，快捷键用作程序命令的键盘快捷键，也可用于菜单或工具栏。 但是，快捷键对应表可用于为没有关联用户界面对象的命令定义组合键。  
  
 可以使用 [类视图](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)将快捷键命令与代码挂接。  
  
 使用快捷键编辑器，可以执行下列操作：  
  
-   [设置快捷键属性](../windows/setting-accelerator-properties.md)  
  
-   [将快捷键与菜单项关联](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [编辑快捷键对应表](../windows/editing-accelerator-tables.md)  
  
-   [使用预定义快捷键](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  使用快捷键编辑器时，可以单击鼠标右键以显示常用命令的快捷菜单。 可用命令取决于指针所指向的内容。  
  
    > [!NOTE]
    >  Windows 不允许创建空快捷键对应表。 如果创建的快捷键对应表中没有任何条目，在保存表时会被自动删除。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Resource Editors](../mfc/resource-editors.md)