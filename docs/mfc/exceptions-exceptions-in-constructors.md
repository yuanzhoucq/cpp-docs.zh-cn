---
title: "异常：构造函数中的异常 | Microsoft Docs"
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
  - "构造函数 [C++], 异常"
  - "异常, 在构造函数中"
  - "引发异常, 在构造函数中"
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 异常：构造函数中的异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当引发构造函数中时的异常，请清除任何对象分配内存和在异常引发之前执行，如 [异常：从的引发的异常的函数](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)说明。  
  
 当在构造函数中引发异常时，在已调用构造函数时,则对象的内存分配。  因此，在异常引发之后，编译器将自动释放对象占用的内存。  
  
 有关更多信息，请参见 [异常：版本在异常对象](../mfc/exceptions-freeing-objects-in-exceptions.md)。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)