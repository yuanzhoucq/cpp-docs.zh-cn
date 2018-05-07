---
title: 编译器警告 （等级 1） C4258 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4258
dev_langs:
- C++
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08a182ed592119fd52247737988810f9ca66b45c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4258"></a>编译器警告（等级 1）C4258
variable： 从定义忽略 for 循环;使用封闭范围中的定义"  
  
 下[/Ze](../../build/reference/za-ze-disable-language-extensions.md)和[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)中, 定义的变量[为](../../cpp/for-statement-cpp.md)循环之后超出范围**为**循环结束。 如果在作用域包含再次使用循环变量，但在封闭的循环中，定义与同名的变量，则会发生此警告**为**循环。 例如：  
  
```  
// C4258.cpp  
// compile with: /Zc:forScope /W1  
int main()  
{  
   int i;  
   {  
      for (int i =0; i < 1; i++)  
         ;  
      i = 20;   // C4258 i (in for loop) has gone out of scope  
   }  
}  
```