---
title: "&lt;utility&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<utility>"
  - "utility/std::<utility>"
  - "std.<utility>"
  - "std::<utility>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "utility 标头"
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;utility&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义有助于构造和管理对象对的标准模板库 \(STL\) 类型、函数和运算符，这些项在每次需要将两个对象视为单个对象时都非常有用。  
  
## 语法  
  
```  
  
#include <utility>  
  
```  
  
## 备注  
 对广泛用于标准 C\+\+ 库中。  对于各种函数，需要将这些对用作参数和返回值，而对于 [map 类](../standard-library/map-class.md)和 [multimap 类](../standard-library/multimap-class.md)等容器，需要将其用作元素类型。  \<map\> 将自动包括 \<utility\> 标头以帮助管理其键\/值对类型元素。  
  
### 类  
  
|||  
|-|-|  
|[tuple\_element](../standard-library/tuple-element-class-utility.md)|一个包装 `pair` 元素的类型的类。|  
|[tuple\_size](../standard-library/tuple-size-class-utility.md)|一个包装 `pair` 元素计数的类。|  
  
### Functions  
  
|||  
|-|-|  
|[forward](../Topic/forward.md)|保留参数的引用类型（`lvalue` 或 `rvalue`），使其不被完美转发掩盖。|  
|[get](../Topic/get%20Function%20%3Cutility%3E.md)|一个从 `pair` 对象获取元素的函数。|  
|[make\_pair](../Topic/make_pair.md)|一个模板帮助程序函数，用于构造类型 `pair` 的对象，其中组件类型基于作为参数传递的数据类型。|  
|[移动](../Topic/move.md)|将传入的参数作为 `rvalue` 引用返回。|  
|[swap](../Topic/swap%20\(%3Cutility%3E\).md)|交换两个 `pair` 对象的元素。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cutility%3E\).md)|测试运算符左侧和右侧的 pair 对象是否不相等。|  
|[operator\=\=](../Topic/operator==%20\(%3Cutility%3E\).md)|测试运算符左侧和右侧的 pair 对象是否相等。|  
|[运算符 \<](../Topic/operator%3C%20\(%3Cutility%3E\).md)|测试运算符左侧的 pair 对象是否小于右侧的 pair 对象。|  
|[运算符 \<\=](../Topic/operator%3C=%20\(%3Cutility%3E\).md)|测试运算符左侧的 pair 对象是否小于或等于右侧的 pair 对象。|  
|[运算符 \>](../Topic/operator%3E%20\(%3Cutility%3E\).md)|测试运算符左侧的 pair 对象是否大于右侧的 pair 对象。|  
|[运算符 \>\=](../Topic/operator%3E=%20\(%3Cutility%3E\).md)|测试运算符左侧的 pair 对象是否大于或等于右侧的 pair 对象。|  
  
### 结构  
  
|||  
|-|-|  
|[标识](../standard-library/identity-structure.md)||  
|[pair](../standard-library/pair-structure.md)|一种类型，它提供了将两个对象视为单个对象的功能。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)