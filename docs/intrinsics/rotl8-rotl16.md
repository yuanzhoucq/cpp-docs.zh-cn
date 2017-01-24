---
title: "_rotl8, _rotl16 | Microsoft Docs"
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
  - "_rotl8"
  - "_rotl16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_rotl16 intrinsic"
  - "_rotl8 intrinsic"
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rotl8, _rotl16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 通过指定的位位置数将输入值旋转到最高有效位 \(MSB\) 左侧。  
  
## 语法  
  
```  
unsigned char _rotl8(     unsigned char value,     unsigned char shift  ); unsigned short _rotl16(     unsigned short value,     unsigned char shift  );  
```  
  
#### 参数  
 \[in\] `value`  
 要旋转的值。  
  
 \[in\] `shift`  
 要旋转的位的数。  
  
## 返回值  
 旋转的值。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`_rotl8`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_rotl16`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 不像左移操作，当执行向左旋转时，离开高端的高序位将移动到最低有效位位置。  
  
## 示例  
  
```  
// rotl.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_rotl8, _rotl16)  
  
int main()  
{  
    unsigned char c = 'A', c1, c2;  
  
    for (int i = 0; i < 8; i++)  
    {  
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,  
               i, _rotl8(c, i));  
    }  
  
    unsigned short s = 0x12;  
    int nBit = 10;  
  
    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",  
            s, nBit, _rotl16(s, nBit));  
}  
```  
  
  **将 0x41 向左旋转 0 位得到 0x41**  
**将 0x41 向左旋转 1 位得到 0x82**  
**将 0x41 向左旋转 2 位得到 0x5**  
**将 0x41 向左旋转 3 位得到 0xa**  
**将 0x41 向左旋转 4 位得到 0x14**  
**将 0x41 向左旋转 5 位得到 0x28**  
**将 0x41 向左旋转 6 位得到 0x50**  
**将 0x41 向左旋转 7 位得到 0xa0**  
**将 unsigned short 0x12 向左旋转 10 位得到 0x4800**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [\_rotr8, \_rotr16](../intrinsics/rotr8-rotr16.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)