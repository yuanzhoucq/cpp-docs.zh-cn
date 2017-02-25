---
title: "编译器警告（等级 1）C4392 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4392"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4392"
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4392
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“signature”: 内部函数的参数个数不正确，应为“number”个参数  
  
 编译器内部对象的函数声明包含错误的参数数目。  结果图像可能无法正确运行。  
  
 若要修复此警告，请更正声明，或删除声明并只使用 \#include 包括适当的头文件。  
  
 下面的示例生成 C4392：  
  
```  
// C4392.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_stream_pd(double *dp);   // C4392  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```