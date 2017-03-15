---
title: "__umulh | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__umulh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__umulh 内部函数"
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __umulh
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 返回两个 64 位无符号整数的产品的高 64 位。  
  
## 语法  
  
```  
unsigned __int64 __umulh(     unsigned __int64 a,     unsigned __int64 b  );  
```  
  
#### 参数  
 \[in\] `a`  
 要相乘的第一个数。  
  
 \[in\] `b`  
 要相乘的第二个数。  
  
## 返回值  
 128 位乘法运算结果的高 64 位。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`__umulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 这些例程只能用作内部函数。  
  
## 示例  
  
```  
// umulh.cpp  
// processor: X64  
#include <cstdio>  
#include <intrin.h>  
  
int main()  
{  
    unsigned __int64 i = 0x10;  
    unsigned __int64 j = 0xFEDCBA9876543210;  
    unsigned __int64 k = i * j; // k has the low 64 bits  
                                // of the product.  
    unsigned __int64 result;  
    result = __umulh(i, j); // result has the high 64 bits  
                            // of the product.  
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);  
    return 0;  
}  
```  
  
  **0x10 \* 0xfedcba9876543210 \= 0xfedcba98765432100**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)