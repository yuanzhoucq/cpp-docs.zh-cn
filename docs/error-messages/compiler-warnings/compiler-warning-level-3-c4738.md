---
title: "编译器警告 (等级 3) C4738 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4738
dev_langs:
- C++
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: ce2db890b7b90eedf5b4456e875a06f8f92b0289
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="compiler-warning-level-3-c4738"></a>编译器警告（等级 3）C4738
将 32 位浮点型结果存储在内存中，可能会降低性能  
  
 C4738 警告或赋值、 强制转换时，结果传递自变量，或其他操作可能需要进行舍入操作用尽了寄存器，并且需要使用 （将溢出） 的内存。 这可能导致性能损失。  
  
 若要解决此警告，并避免舍入，编译与[/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md)或使用`double`而不是`float`。  
  
 若要解决此警告，并避免不足寄存器，更改计算顺序，并修改的使用内联  
  
 默认情况下，此警告处于关闭状态。 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4738:  
  
```  
// C4738.cpp  
// compile with: /c /fp:precise /O2 /W3  
// processor: x86  
#include <stdio.h>  
  
#pragma warning(default : 4738)  
  
float func(float f)  
{  
    return f;  
}  
  
int main()  
{  
    extern float f, f1, f2;  
    double d = 0.0;  
  
    f1 = func(d);  
    f2 = (float) d;  
    f = f1 + f2;   // C4738  
    printf_s("%f\n", f);  
}  
```
