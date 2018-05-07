---
title: 编译器错误 C2178 |Microsoft 文档
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3727a66554b2e128061820df160c02a1370ebb74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2178"></a>编译器错误 C2178  
  
*标识符*不能使用声明*说明符*说明符  
  
A`mutable`在声明中，已使用说明符，但此上下文中不允许使用说明符。  
  
`mutable`说明符可以只能应用于类数据成员的名称和不能应用于声明名称`const`或`static`，和不能应用于引用的成员。  
  
## <a name="example"></a>示例  
  
下面的示例演示如何可能发生 C2178，以及如何修复此错误。  
  
```  
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```  
