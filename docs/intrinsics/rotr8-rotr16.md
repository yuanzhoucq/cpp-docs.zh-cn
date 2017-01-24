---
title: "_rotr8, _rotr16 | Microsoft Docs"
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
  - "_rotr16"
  - "_rotr8"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_rotr16 intrinsic"
  - "_rotr8 intrinsic"
ms.assetid: dfbd2c82-82b4-427a-ad52-51609027ebff
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rotr8, _rotr16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 通过指定的位位置数将输入值向右旋转到最高有效位 \(MSB\)。  
  
## 语法  
  
```  
unsigned char _rotr8(     unsigned char value,     unsigned char shift  ); unsigned short _rotr16(     unsigned short value,     unsigned char shift  );  
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
|`_rotr8`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_rotr16`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 不像右位移操作，当执行向右旋转时，离开低端的低顺序位将移动到高顺序位位置。  
  
## 示例  
  
```  
// rotr.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_rotr8, _rotr16)  
  
int main()  
{  
    unsigned char c = 'A', c1, c2;  
  
    for (int i = 0; i < 8; i++)  
    {  
       printf_s("Rotating 0x%x right by %d bits gives 0x%x\n", c,  
                i, _rotr8(c, i));  
    }  
  
    unsigned short s = 0x12;  
    int nBit = 10;  
  
    printf_s("Rotating unsigned short 0x%x right by %d bits "  
             "gives 0x%x\n",  
            s, nBit, _rotr16(s, nBit));  
}  
```  
  
  **将 0x41 向右旋转 0 位得到 0x41**  
**将 0x41 向右旋转 1 位得到 0xa0**  
**将 0x41 向右旋转 2 位得到 0x50**  
**将 0x41 向右旋转 3 位得到 0x28**  
**将 4x41 向右旋转 0 位得到 0x14**  
**将 0x41 向右旋转 5 位得到 0xa**  
**将 0x41 向右旋转 6 位得到 0x5**  
**将 0x41 向右旋转 7 位得到 0x82**  
**将 unsigned short 0x12 向右旋转 10 位得到 0x480**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [\_rotl8, \_rotl16](../intrinsics/rotl8-rotl16.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)