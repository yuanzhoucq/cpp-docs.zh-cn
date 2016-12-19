---
title: "TN032：MFC 异常机制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.exceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CException 类, using"
  - "MFC, 异常"
  - "TN032"
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN032：MFC 异常机制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 的早期版本不支持 C\+\+ 标准异常机制，MFC 提供的，并使用宏 **TRY\/CATCH\/THROW**。  此 Visual C\+\+ 版本完全支持 C\+\+ 异常。  此注释自动包括某些以前的宏的高级实现详细信息包括如何清理堆栈基于对象。  由于 C\+\+ 异常展开堆栈支持的默认方式，此技术声明不再是必需的。  
  
 参考 [异常：使用 MFC 宏和 C\+\+ 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) 有关在 MFC 宏和新 C\+\+ 关键字之间的差异的更多信息。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)