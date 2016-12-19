---
title: "_BitScanForward, _BitScanForward64 | Microsoft Docs"
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
  - "_BitScanForward"
  - "_BitScanForward_cpp"
  - "_BitScanForward64_cpp"
  - "_BitScanForward64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_BitScanForward intrinsic"
  - "BitScanForward intrinsic"
  - "bsf instruction"
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _BitScanForward, _BitScanForward64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 从设置位 \(1\) 的最低有效位 \(LSB\) 到最高有效位 \(MSB\) 搜索掩码数据。  
  
## 语法  
  
```  
unsigned char _BitScanForward(    unsigned long * Index,    unsigned long Mask ); unsigned char _BitScanForward64(    unsigned long * Index,    unsigned __int64 Mask );  
```  
  
#### 参数  
 \[out\] `Index`  
 已使用找到的第一个设置位 \(1\) 的位位置加载。  
  
 \[in\] `Mask`  
 要搜索的 32 位或 64 位值。  
  
## 返回值  
 如果掩码为零，则为 0；否则为非零值。  
  
## 备注  
 如果找到一个设置位，则将在第一个参数中返回已找到的第一个设置位的位位置。  如果没有发现任何设置位，则返回 0；否则返回 1。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`_BitScanForward`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_BitScanForward64`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 示例  
  
```  
// BitScanForward.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanForward)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanForward(&index, mask);  
   if (isNonzero)  
   {  
      cout << "Mask: " << mask << " Index: " << index << endl;  
   }  
   else  
   {  
      cout << "No set bits found.  Mask is zero." << endl;  
   }  
}  
```  
  
## 输入  
  
```  
12  
```  
  
## 示例输出  
  
```  
Enter a positive integer as the mask:   
Mask: 12 Index: 2  
```  
  
### 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)