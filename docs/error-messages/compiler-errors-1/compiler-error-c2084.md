---
title: 编译器错误 C2084 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce1510dd6e78b8774d3cc433f583c16cdbb8d06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2084"></a>编译器错误 C2084
函数*函数*已具有一个主体  
  
 已定义的函数。  
  
 在 Visual Studio 2002 之前, 的 Visual c + + 的版本  
  
-   编译器将接受解析为相同的实际类型的多个模板专用化，尽管其他定义将永远不可用。 现在，编译器检测到这些多个定义。  
  
-   `__int32` 和`int`则被视为单独的类型。 编译器现在将`__int32`的同义词`int`。 这意味着，编译器检测到多个定义如果函数重载两侧`__int32`和`int`，并且产生错误。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2084:  
  
```cpp  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
若要更正此错误，删除重复的定义：  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```