---
title: "编译器错误 C2084 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a1fe070ffe0988b22484d3eb162377a8723c72ee
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2084"></a>编译器错误 C2084
函数*函数*已具有一个主体  
  
 已定义的函数。  
  
 在 Visual Studio 2002 之前, 的 Visual c + + 的版本  
  
-   编译器将接受解析为相同的实际类型的多个模板专用化，尽管其他定义将永远不可用。 现在，编译器检测到这些多个定义。  
  
-   `__int32`和`int`则被视为单独的类型。 编译器现在将`__int32`的同义词`int`。 这意味着，编译器检测到多个定义如果函数重载两侧`__int32`和`int`，并且产生错误。  
  
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
