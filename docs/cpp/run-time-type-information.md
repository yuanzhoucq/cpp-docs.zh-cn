---
title: "运行时类型信息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b0b0124a69a0110bda94055964fbcdb54e5a754
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="run-time-type-information"></a>运行时类型信息
运行时类型信息 (RTTI) 是一种允许在程序执行过程中确定对象的类型的机制。 RTTI 已添加到 C++ 语言中，因为许多类库供应商将自行实现此功能。 这会导致库之间出现不兼容的情况。 因此，显而易见的是，需要语言级别的对运行时类型信息的支持。  
  
 为了清楚起见，此 RTTI 的讨论几乎完全是针对指针展开的。 但讨论的概念也适用于引用。  
  
 有三个针对运行时类型信息的 C++ 语言元素：  
  
-   [Dynamic_cast](../cpp/dynamic-cast-operator.md)运算符。  
  
     用于多态类型的转换。  
  
-   [Typeid](../cpp/typeid-operator.md)运算符。  
  
     用于标识对象的确切类型。  
  
-   [Type_info](../cpp/type-info-class.md)类。  
  
     用于保留由 `typeid` 运算符返回的类型信息。  
  
## <a name="see-also"></a>请参阅  
 [强制转换](../cpp/casting.md)