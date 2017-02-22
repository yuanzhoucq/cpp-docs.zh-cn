---
title: "窗口过程入口点 | Microsoft Docs"
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
  - "入口点, 窗口过程"
  - "MFC, 管理状态数据"
  - "状态管理, 窗口过程"
  - "窗口过程入口点"
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 窗口过程入口点
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要保护 MFC 窗口过程模块，静态链接具有特定窗口过程实现。  当模块连接到MFC时，链接操作自动发生。  此窗口过程使用 `AFX_MANAGE_STATE` 宏可正确设置的有效模块状态，则调用 **AfxWndProc**，而委托的适当成员函数 `CWnd``WindowProc` 派生的对象。  
  
## 请参阅  
 [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)