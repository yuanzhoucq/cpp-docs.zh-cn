---
title: "__shiftleft128 | Microsoft Docs"
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
  - "__shiftleft128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__shiftleft128 intrinsic"
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __shiftleft128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将 128 位数量（表示为两个 64 位数量 `LowPart` 和 `HighPart`）按 `Shift` 指定的位数左移，返回高 64 位结果。  
  
## 语法  
  
```  
unsigned __int64 __shiftleft128(     unsigned __int64 LowPart,     unsigned __int64 HighPart,     unsigned char Shift  );  
```  
  
#### 参数  
 \[in\] `LowPart`  
 要位移的 128 位数量的低 64 位。  
  
 \[in\] `HighPart`  
 要位移的 128 位数量的高 64 位。  
  
 \[in\] `Shift`  
 要位移的位数。  
  
## 返回值  
 高 64 位的结果。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`__shiftleft128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `Shift` 值始终是模 64，如果调用 `__shiftleft128(1, 0, 64)`，该函数将向左位移低部分 `0` 位并返回高部分的 `0` 而不是另外预期的 `1`。  
  
## 示例  
  
```  
// shiftleft128.c  
// processor: IPF, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__shiftleft128, __shiftright128)  
  
int main()  
{  
    unsigned __int64 i = 0x1I64;  
    unsigned __int64 j = 0x10I64;  
    unsigned __int64 ResultLowPart;  
    unsigned __int64 ResultHighPart;  
  
    ResultLowPart = i << 1;  
    ResultHighPart = __shiftleft128(i, j, 1);  
  
    // concatenate the low and high parts padded with 0's  
    // to display correct hexadecimal 128 bit values  
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);  
  
    ResultHighPart = j >> 1;  
    ResultLowPart = __shiftright128(i, j, 1);  
  
    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);    
}  
```  
  
  **0x100000000000000001 \<\< 1 \= 0x200000000000000002**  
**0x100000000000000001 \>\> 1 \= 0x080000000000000000**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [\_\_shiftright128](../intrinsics/shiftright128.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)