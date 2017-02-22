---
title: "_HAS_ITERATOR_DEBUGGING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_HAS_ITERATOR_DEBUGGING"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_HAS_ITERATOR_DEBUGGING"
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _HAS_ITERATOR_DEBUGGING
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义迭代器在调试功能是否启用调试版本。  默认情况下，调试启用迭代器。  有关详细信息，请参阅[调试迭代器支持](../standard-library/debug-iterator-support.md)。  
  
> [!IMPORTANT]
>  使用 `_ITERATOR_DEBUG_LEVEL` 控制 `_HAS_ITERATOR_DEBUGGING`。  有关详细信息，请参阅[\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## 备注  
 若要启用迭代器调试调试版本中，将 **\_HAS\_ITERATOR\_DEBUGGING** 设置为 1:  
  
```  
#define _HAS_ITERATOR_DEBUGGING 1  
```  
  
 **\_HAS\_ITERATOR\_DEBUGGING** 不能设置为 1。零售版本。  
  
 若要禁用迭代器调试调试版本中，将 **\_HAS\_ITERATOR\_DEBUGGING** 设置为 0:  
  
```  
#define _HAS_ITERATOR_DEBUGGING 0  
```  
  
## 请参阅  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)   
 [调试迭代器支持](../standard-library/debug-iterator-support.md)   
 [经过检查的迭代器](../standard-library/checked-iterators.md)   
 [安全库：C\+\+ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)