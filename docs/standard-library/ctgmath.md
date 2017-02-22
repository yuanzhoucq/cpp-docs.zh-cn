---
title: "&lt;ctgmath&gt; | Microsoft Docs"
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
ms.assetid: ff521893-f445-4dc8-a2f6-699185bb7024
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;ctgmath&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

实际上，包括标准 C\+\+ 库标头 \<ccomplex\> 和 \<cmath\>，用于提供等效于 \<tgmath.h\> 的泛型类型算术宏。  
  
## 语法  
  
```  
  
#include <ctgmath>  
  
```  
  
## 备注  
 标准 C 库标头 \<tgmath.h\> 的功能通过 \<ccomplex\> 和 \<cmath\> 中的重载来提供。  
  
 包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。  
  
## 请参阅  
 [\<ccomplex\>](../standard-library/ccomplex.md)   
 [\<cmath\>](../standard-library/cmath.md)   
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [STL 概述](../standard-library/cpp-standard-library-overview.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)