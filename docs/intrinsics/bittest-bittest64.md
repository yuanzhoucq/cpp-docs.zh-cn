---
title: "_bittest, _bittest64 | Microsoft Docs"
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
  - "_bittest64"
  - "_bittest_cpp"
  - "_bittest64_cpp"
  - "_bittest"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bittest intrinsic"
  - "_bittest64 intrinsic"
  - "bt instruction"
ms.assetid: 15e62afb-abea-4ee7-a6b1-13efa2034937
caps.latest.revision: 19
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _bittest, _bittest64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `bt` 指令，从而检查地址 `a` 的位置 `b` 中的位，并返回该位的值。  
  
## 语法  
  
```  
unsigned char _bittest(    long *a,    long b ); unsigned char _bittest64(    __int64 *a,    __int64 b );  
```  
  
#### 参数  
 \[in\] `a`  
 指向要检查的内存的指针。  
  
 \[in\] `b`  
 要测试的位位置。  
  
## 返回值  
 指定位置的位。  
  
## 要求  
  
|内部函数|体系结构|Header|  
|----------|----------|------------|  
|`_bittest`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_bittest64`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
  
## 备注  
 此例程仅可用作内部函数。  
  
## 示例  
  
```  
// bittest.cpp  
// processor: x86, ARM, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
long num = 78002;  
  
int main()  
{  
    unsigned char bits[32];  
    long nBit;  
  
    printf_s("Number: %d\n", num);  
  
    for (nBit = 0; nBit < 31; nBit++)  
    {  
        bits[nBit] = _bittest(&num, nBit);  
    }  
  
    printf_s("Binary representation:\n");  
    while (nBit--)  
    {  
        if (bits[nBit])  
            printf_s("1");  
        else  
            printf_s("0");  
    }  
}  
```  
  
  **编号： 78002**  
**二进制表示形式：**  
**0000000000000010011000010110010**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)