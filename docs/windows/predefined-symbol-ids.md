---
title: "Predefined Symbol IDs | Microsoft Docs"
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
  - "symbols, predefined IDs"
  - "predefined symbol IDs"
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Predefined Symbol IDs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

开始新项目时，根据项目类型预定义了一些符号 ID 供你使用。  这些符号 ID 支持 MFC 等各种库和项目类型。  它们表示通常包含于任何应用程序或硬件项（如鼠标或打印机）动作中的常见任务。  
  
 处理资源时，这些符号 ID 变得很重要。  它们可用于编辑快捷键表，其中一些已与虚拟键相关联。  还可以通过[“属性”窗口](../Topic/Properties%20Window.md)使用它们。  你可以将任何预定义的符号 ID 分配给新资源，也可以向它们分配快捷键，与该符号 ID 关联的功能会自动与该密钥组合关联。  
  
 以下具有预定义符号的库将显示为项目的一部分：  
  
-   [MFC 预定义的符号](../windows/mfc-predefined-symbols.md)  
  
-   [ATL 预定义的符号](../windows/atl-predefined-symbols.md)  
  
-   [Win32 预定义符号](../windows/win32-predefined-symbols.md)  
  
    > [!NOTE]
    >  预定义的符号始终是只读的。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32、MFC 或 ATL  
  
## 请参阅  
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)