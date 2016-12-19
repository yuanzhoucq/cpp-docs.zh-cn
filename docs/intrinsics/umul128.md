---
title: "_umul128 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__umul128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__umul128 intrinsic"
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _umul128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 乘以作为前两个参数传入的两个 64 位无符号整数，将产品的高 64 位置于由 `HighProduct` 指向的 64 位无符号整数，并返回产品的低 64 位。  
  
## 语法  
  
```  
unsigned __int64 _umul128(     unsigned __int64 Multiplier,     unsigned __int64 Multiplicand,     unsigned __int64 *HighProduct  );  
```  
  
#### 参数  
 \[in\] `Multiplier`  
 要相乘的第一个 64 位整数。  
  
 \[in\] `Multiplicand`  
 要相乘的第二个 64 位整数。  
  
 \[out\] `HighProduct`  
 产品的高 64 位。  
  
## 返回值  
 产品的低 64 位。  
  
## 要求  
  
|内部函数|体系结构|Header|  
|----------|----------|------------|  
|`_umul128`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
  
## 示例  
  
```  
// umul128.c  
// processor: IPF, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_umul128)  
  
int main()  
{  
    unsigned __int64 a = 0x0fffffffffffffffI64;  
    unsigned __int64 b = 0xf0000000I64;  
    unsigned __int64 c, d;  
  
    d = _umul128(a, b, &c);  
  
    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);  
}  
```  
  
  **0xfffffffffffffff \* 0xf0000000 \= 0xeffffffffffffff10000000**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)