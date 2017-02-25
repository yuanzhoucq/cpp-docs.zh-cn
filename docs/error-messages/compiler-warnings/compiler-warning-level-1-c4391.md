---
title: "编译器警告（等级 1）C4391 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4391"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4391"
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4391
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“signature”: 错误的内部函数返回类型，应为“type”  
  
 编译器内部对象的函数声明包含错误的返回类型。  结果图像可能无法正确运行。  
  
 若要修复此警告，请更正声明，或删除声明并只使用 \#include 包括适当的头文件。  
  
 下面的示例生成 C4391：  
  
```  
// C4391.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_load_ss(float *p);   // C4391  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```