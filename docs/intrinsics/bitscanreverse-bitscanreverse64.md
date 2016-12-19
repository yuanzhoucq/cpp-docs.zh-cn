---
title: "_BitScanReverse, _BitScanReverse64 | Microsoft Docs"
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
  - "_BitScanReverse64"
  - "_BitScanReverse_cpp"
  - "_BitScanReverse"
  - "_BitScanReverse64_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_BitScanReverse intrinsic"
  - "BitScanReverse intrinsic"
  - "bsr instruction"
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _BitScanReverse, _BitScanReverse64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 从设置位 \(1\) 的最高有效位 \(MSB\) 到最低有效位 \(LSB\) 搜索掩码数据。  
  
## 语法  
  
```  
unsigned char _BitScanReverse(    unsigned long * Index,    unsigned long Mask ); unsigned char _BitScanReverse64(    unsigned long * Index,    unsigned __int64 Mask );  
```  
  
#### 参数  
 \[out\] `Index`  
 已使用找到的第一个设置位 \(1\) 的位位置加载。  
  
 \[in\] `Mask`  
 要搜索的 32 位或 64 位值。  
  
## 返回值  
 如果设定 `Index`，则为非零，如果未发现设置位，则为 0。  
  
## 要求  
  
|内部函数|体系结构|Header|  
|----------|----------|------------|  
|`_BitScanReverse`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_BitScanReverse64`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]||  
  
## 示例  
  
```  
// BitScanReverse.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanReverse)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanReverse(&index, mask);  
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
Mask: 12 Index: 3  
```  
  
### 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)