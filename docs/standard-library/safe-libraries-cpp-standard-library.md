---
title: "安全库：C++ 标准库 | Microsoft Docs"
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
  - "_SCL_SECURE_NO_DEPRECATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "安全库"
  - "安全库，标准 C++ 库"
  - "安全标准 C++ 库"
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 安全库：C++ 标准库
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

已对随附于 Visual C\+\+ 的库（包括标准 C\+\+ 库）实施了多项功能增强以使它们更加安全。  
  
 已将标准 C\+\+ 库中的多个方法确定为具有潜在的不安全性，因为它们可能导致缓冲区溢出或其他代码缺陷。 建议不要使用这些方法，已创建了更安全的新方法来替代这些方法。 这些新方法均以 `_s` 结尾。  
  
 还实施了多项功能增强以提升迭代器和算法的安全性。 有关详细信息，请参阅 [经过检查的迭代器](../standard-library/checked-iterators.md)、[调试迭代器支持](../standard-library/debug-iterator-support.md) 和 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## 备注  
 下表列出了可能不安全的标准 C\+\+ 库方法，以及更安全的等效方法：  
  
|可能不安全的方法|更安全的等效方法|  
|--------------|--------------|  
|[basic\_string::copy](../Topic/basic_string::copy.md)|[basic\_string::\_Copy\_s](../Topic/basic_string::_Copy_s.md)|  
|[char\_traits::copy](../Topic/char_traits::copy.md)|[char\_traits::\_Copy\_s](../Topic/char_traits::_Copy_s.md)|  
  
 如果调用以上任何一种潜在不安全的方法或如果错误使用迭代器，则编译器将生成 [编译器警告（等级 3）C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 有关如何禁用这些警告的信息，请参阅 [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
## 本节内容  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)  
  
 [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md)  
  
 [经过检查的迭代器](../standard-library/checked-iterators.md)  
  
 [调试迭代器支持](../standard-library/debug-iterator-support.md)  
  
## 请参阅  
 [STL 概述](../standard-library/cpp-standard-library-overview.md)