---
title: "_bittestandreset, _bittestandreset64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_bittestandreset64_cpp"
  - "_bittestandreset"
  - "_bittestandreset_cpp"
  - "_bittestandreset64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bittestandreset intrinsic"
  - "_bittestandreset64 intrinsic"
  - "btr instruction"
ms.assetid: 8dad63bb-a051-4cd7-a793-3357537dfeaf
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _bittestandreset, _bittestandreset64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成可以检查地址 `a` 的位 `b`，返回其当前值，然后将位重新设置为 0 的指令。  
  
## 语法  
  
```  
unsigned char _bittestandreset(    long *a,    long b ); unsigned char _bittestandreset64(    __int64 *a,    __int64 b );  
```  
  
#### 参数  
 \[in, out\] `a`  
 指向要检查的内存的指针。  
  
 \[in\] `b`  
 要测试的位位置。  
  
## 返回值  
 指定位置的位。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`_bittestandreset`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_bittestandreset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此例程仅可用作内部函数。  
  
## 示例  
  
```  
// bittestandreset.cpp  
// processor: x86, IPF, x64  
#include <stdio.h>  
#include <limits.h>  
#include <intrin.h>  
  
#pragma intrinsic(_bittestandreset)  
  
// Check the sign bit and reset to 0 (taking the absolute value)  
// Returns 0 if the number is positive or zero  
// Returns 1 if the number is negative  
unsigned char absolute_value(long* p)  
{  
   const int SIGN_BIT = 31;  
   return _bittestandreset(p, SIGN_BIT);  
}  
  
int main()  
{  
    long i = -112;  
    unsigned char result;  
  
    // Check the sign bit and reset to 0 (taking the absolute value)  
  
    result = absolute_value(&i);  
    if (result == 1)  
        printf_s("The number was negative.\n");     
}  
```  
  
  **此数为负数。**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)