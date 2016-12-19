---
title: "调试和异常类 | Microsoft Docs"
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
  - "vc.classes.debug"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调试 [MFC], 用于调试的类"
  - "调试 [MFC], 异常类"
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 调试和异常类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些类提供支持调试动态内存分配，并支持传递来自将引发异常函数的异常信息。  
  
 使用类[CDumpContext](../mfc/reference/cdumpcontext-class.md) 和[CMemoryState](../mfc/reference/cmemorystate-structure.md) ，在开发期间帮助调试，如 [调试 MFC 应用程序](../Topic/MFC%20Debugging%20Techniques.md)所述。  使用 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 确定在运行时中的所有对象类，如 [访问运行时信息类](../mfc/accessing-run-time-class-information.md)文章所述。  框架使用 `CRuntimeClass` 动态创建特定类的对象。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)