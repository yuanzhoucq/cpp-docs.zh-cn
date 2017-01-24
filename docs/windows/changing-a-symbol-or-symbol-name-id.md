---
title: "Changing a Symbol or Symbol Name (ID) | Microsoft Docs"
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
  - "vc.editors.symbol.changing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbol names"
  - "symbols, names"
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing a Symbol or Symbol Name (ID)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建新资源或资源对象时，开发环境会向它分配默认符号名，例如 IDD\_DIALOG1。  可以使用[属性窗口](../Topic/Properties%20Window.md)更改默认符号名，或更改已与资源关联的任何符号的名称。  
  
### 更改资源的符号名  
  
1.  在[资源视图](../windows/resource-view-window.md)中，选择资源。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**“属性”**窗口中，在**“ID”**框中输入新符号名，或从现有符号列表中进行选择。  
  
     如果输入新符号名，则会自动向它赋值。  
  
 可以使用[“资源符号”对话框](../windows/resource-symbols-dialog-box.md)更改当前未分配给资源的符号的名称。  有关详细信息，请参阅[更改未分配的符号](../windows/changing-unassigned-symbols.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Symbol Name Restrictions](../windows/symbol-name-restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)