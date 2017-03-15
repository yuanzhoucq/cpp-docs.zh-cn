---
title: "消息处理程序 | Microsoft Docs"
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
  - "命令处理, 消息处理程序"
  - "处理程序"
  - "处理程序, 命令"
  - "处理程序, message"
  - "消息处理程序"
  - "消息处理, 消息处理程序函数"
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 消息处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 中，私有的 *处理程序* 函数处理每一单独的消息。  消息处理函数是类的成员函数。  此文档可交换使用术语 *消息处理程序成员函数*、*消息处理函数*、*消息处理程序*和 *处理程序*。  消息处理程序调用“命令处理程序”。  
  
 写入消息处理程序考虑工作的一大比例在使用编写应用程序的框架。  本文系列介绍消息处理机制的工作方式。  
  
 消息的处理程序执行什么？  在执行您想要执行响应该消息。  使用类的属性窗口，使用源代码编辑器，可以创建处理程序，然后填写处理程序的代码。  
  
 您可以使用任何 Microsoft Visual C\+\+ 和 MFC 的功能编写处理程序。  有关所有类列表，请参见" *MFC 参考"中的*[概述类库](../mfc/class-library-overview.md)。  
  
## 请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)