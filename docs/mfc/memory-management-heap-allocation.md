---
title: "内存管理：堆分配 | Microsoft Docs"
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
  - "删除运算符, 使用调试 MFC"
  - "检测内存泄漏"
  - "堆分配"
  - "堆分配, 描述"
  - "内存分配, 堆内存"
  - "内存泄漏, 检测"
  - "内存, 检测泄漏"
  - "new 运算符, 使用调试 MFC"
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 内存管理：堆分配
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

堆为程序的内存分配需要保留的。  除了该区域程序代码和堆栈外。  典型的 C 程序使用函数 `malloc` 和 **free** 分配和释放堆内存。  MFC 的" Debug "版本提供内置 C\+\+ **new** 和 **删除** 运算符的修改版本分配和释放堆中内存的对象。  
  
 当使用 **new** 和 **删除** 取代 `malloc` 和 **free**时，可以利用类库的内存管理调试增强，很有用。检测内存泄漏。  在生成与 MFC 版本的时发布程序，**new** 和 **删除** 运算符的标准版本提供了一种有效的方法分配和释放内存 \(MFC 发布版本不提供修改这些运算符版本\)。  
  
 请注意上堆中分配的对象的总大小受系统可用的虚拟内存只限制。  
  
## 请参阅  
 [内存管理](../mfc/memory-management.md)