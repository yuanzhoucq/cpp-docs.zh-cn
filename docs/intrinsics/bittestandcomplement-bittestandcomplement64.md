---
title: "_bittestandcomplement, _bittestandcomplement64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_bittestandcomplement64"
  - "_bittestandcomplement64_cpp"
  - "_bittestandcomplement_cpp"
  - "_bittestandcomplement"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bittestandcomplement intrinsic"
  - "_bittestandcomplement64 intrinsic"
  - "btc instruction"
ms.assetid: 53fa12dd-835e-4e5d-baec-a431c8678806
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _bittestandcomplement, _bittestandcomplement64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成可以检查地址 `a` 的位 `b` 的指令，返回其当前值，然后将位设置为该值的补充值。  
  
## 语法  
  
```  
unsigned char _bittestandcomplement(    long *a,    long b ); unsigned char _bittestandcomplement64(    __int64 *a,    __int64 b );  
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
|`_bittestandcomplement`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_bittestandcomplement64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此例程仅可用作内部函数。  
  
## 示例  
  
```  
// bittestandcomplement.cpp  
// processor: x86, IPF, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_bittestandcomplement)  
#ifdef _M_AMD64  
#pragma intrinsic(_bittestandcomplement64)  
#endif  
  
int main()  
{  
   long i = 1;  
   __int64 i64 = 0x1I64;  
   unsigned char result;  
   printf("Initial value: %d\n", i);  
   printf("Testing bit 1\n");  
   result = _bittestandcomplement(&i, 1);  
   printf("Value changed to %d, Result: %d\n", i, result);  
#ifdef _M_AMD64  
   printf("Testing bit 0\n");  
   result = _bittestandcomplement64(&i64, 0);  
   printf("Value changed to %I64d, Result: %d\n", i64, result);  
#endif  
}  
```  
  
## 示例输出  
  
```  
Initial value: 1  
Testing bit 1  
Value changed to 3, Result: 0  
Testing bit 0  
Value changed to 0, Result: 1  
```  
  
### 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)