---
title: "Active 技术和 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Active 技术 [C++]"
  - "本机 [C++], DLL"
  - "DLL [C++], Active 技术"
  - "进程内服务器 DLL"
  - "MFC DLL [C++], Active 技术"
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Active 技术和 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Active 技术使对象服务器得以完全在 DLL 内部实现。  这类服务器称为“进程内服务器”。  MFC 不完全支持在进程内服务器中实现所有可视化编辑功能，主要是因为 Active 技术没有为服务器提供挂钩到容器的主消息循环中的方法。  MFC 需要访问容器应用程序的消息循环以处理快捷键和空闲时间处理。  
  
 如果正在编写自动化服务器并且该服务器没有用户界面，可以使该服务器成为进程内服务器并将其完全放入 DLL。  
  
## 您想进一步了解什么？  
  
-   [自动化服务器](../mfc/automation-servers.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)