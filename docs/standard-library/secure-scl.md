---
title: "_SECURE_SCL | Microsoft Docs"
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
  - "_SECURE_SCL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_SECURE_SCL"
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _SECURE_SCL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义是否启用。[经过检查的迭代器](../standard-library/checked-iterators.md) 如果定义为 1，不安全的迭代器使用导致运行时错误，且程序终止。  如果定义为 0，都会检查的迭代器被禁用。  在调试模式中，**\_SECURE\_SCL** 的默认值为 1，这意味着检查的迭代器支持。  在发布模式，`_SECURE_SCL` 的默认值为 0。  
  
> [!IMPORTANT]
>  使用 `_ITERATOR_DEBUG_LEVEL` 控制 `_SECURE_SCL`。  有关详细信息，请参阅[\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## 备注  
 若要关闭检查迭代器，将 **\_SECURE\_SCL** 设置为 1:  
  
```  
#define _SECURE_SCL 1  
```  
  
 若要禁用 CHECK 迭代器，将 **\_SECURE\_SCL** 设置为 0:  
  
```  
#define _SECURE_SCL 0  
```  
  
 有关如何禁用有关检查的迭代器的警告的信息，请参见 [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
## 请参阅  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)   
 [经过检查的迭代器](../standard-library/checked-iterators.md)   
 [调试迭代器支持](../standard-library/debug-iterator-support.md)   
 [安全库：C\+\+ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)