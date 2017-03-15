---
title: "编译器警告（等级 1）C4730 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4730"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4730"
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4730
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“main”: 混合使用 \_m64 和浮点表达式可能导致错误的代码  
  
 函数使用 [\_\_m64](../../cpp/m64.md) 和 **float**\/**double** 类型。  由于 MMX 和浮点寄存器共享相同的物理寄存器空间（不能同时使用），在同一函数中使用 `__m64` 和 **float**\/**double** 类型会导致数据损坏，可能引起异常。  
  
 若要在同一函数中安全地使用 `__m64` 和浮点类型，使用其中一种类型的每个指令应该用内部 **\_m\_empty\(\)**（适用于 MMX）或 **\_m\_femms\(\)**（适用于 3DNow\!™）进行分隔。  
  
 下面的示例生成 C4730：  
  
```  
// C4730.cpp  
// compile with: /W1  
// processor: x86  
#include "mmintrin.h"  
  
void func(double)  
{  
}  
  
int main(__m64 a, __m64 b)  
{  
   __m64 m;  
   double f;  
   f = 1.0;  
   m = _m_paddb(a, b);  
   // uncomment the next line to resolve C4730  
   // _m_empty();  
   func(f * 3.0);   // C4730  
}  
```