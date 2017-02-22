---
title: "编译器警告（等级 3）C4738 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4738"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4738"
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 3）C4738
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将 32 位浮点型结果存储在内存中，可能会降低性能  
  
 C4738 警告：赋值、强制转换、传递的参数或其他操作的结果可能需要舍入，或者操作由于寄存器不足而需要使用内存（泄漏）。  这可能导致性能降低。  
  
 若要消除此警告并且避免舍入，请用 [\/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md) 进行编译或者使用 `double` 而不是 `float`。  
  
 若要消除此警告并且避免寄存器不足，请更改计算的顺序并修改内联的使用  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 示例  
 下面的示例生成 C4738：  
  
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