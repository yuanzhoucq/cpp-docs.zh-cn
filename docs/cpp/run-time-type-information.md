---
title: "运行时类型信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RTTI 编译器选项"
  - "运行时, 类型检查"
  - "运行时检查, 类型检查"
  - "运行时类型信息"
  - "类型信息, 运行时类型检查"
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 运行时类型信息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

运行时类型信息 \(RTTI\) 是一种允许在程序执行过程中确定对象的类型的机制。  RTTI 已添加到 C\+\+ 语言中，因为许多类库供应商将自行实现此功能。  这会导致库之间出现不兼容的情况。  因此，显而易见的是，需要语言级别的对运行时类型信息的支持。  
  
 为了清楚起见，此 RTTI 的讨论几乎完全是针对指针展开的。  但讨论的概念也适用于引用。  
  
 有三个针对运行时类型信息的 C\+\+ 语言元素：  
  
-   [dynamic\_cast](../cpp/dynamic-cast-operator.md) 运算符。  
  
     用于多态类型的转换。  
  
-   [typeid](../cpp/typeid-operator.md) 运算符。  
  
     用于标识对象的确切类型。  
  
-   [type\_info](../cpp/type-info-class.md) 类。  
  
     用于保留由 `typeid` 运算符返回的类型信息。  
  
## 请参阅  
 [强制转换](../cpp/casting.md)