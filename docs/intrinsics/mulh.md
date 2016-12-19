---
title: "__mulh | Microsoft Docs"
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
  - "__mulh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__mulh 内部函数"
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __mulh
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 返回两个 64 位有符号整数的乘积的高 64 位。  
  
## 语法  
  
```  
__int64 __mulh(   
   __int64 a,   
   __int64 b   
);  
```  
  
#### 参数  
 \[in\] `a`  
 要相乘的第一个数字。  
  
 \[in\] `b`  
 要相乘的第二个数字。  
  
## 返回值  
 乘法的 128 位结果的高 64 位。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__mulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 示例  
  
```  
// mulh.cpp  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__mulh)  
  
int main()  
{  
    __int64 a = 0x0fffffffffffffffI64;  
    __int64 b = 0xf0000000I64;  
  
    __int64 result = __mulh(a, b); // the high 64 bits  
    __int64 result2 = a * b; // the low 64 bits  
  
    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",  
             a, b, result, result2);  
}  
```  
  
  **0xfffffffffffffff \* 0xf0000000 \= 0xeffffffffffffff10000000**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)