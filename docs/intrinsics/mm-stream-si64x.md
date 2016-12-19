---
title: "_mm_stream_si64x | Microsoft Docs"
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
  - "_mm_stream_si64x"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movnti 指令"
  - "_mm_stream_si64x intrinsic"
ms.assetid: 114c2cd0-085f-41aa-846e-87bdd56c9ee7
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mm_stream_si64x
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 MOVNTI 命令。  编写在 `Source` 的数据。 `Dest`指定的内存位置，而污染缓存。  
  
## 语法  
  
```  
void _mm_stream_si64x(   
   __int64 * Dest,   
   __int64 Source   
);  
```  
  
#### 参数  
 \[out\] `Dest`  
 为位置的指针编写的源数据。  
  
 \[in\] `Source`  
 写入的数据。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_mm_stream_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 示例  
  
```  
// _mm_stream_si64x.c  
// processor: x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_mm_stream_si64x)  
  
int main()  
{  
    __int64 val = 0xFFFFFFFFFFFFI64;  
    __int64 a[10];  
  
    memset(a, 0, sizeof(a));  
    _mm_stream_si64x(a+1, val);  
    printf_s( "%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);   
}  
```  
  
  **0 ffffffffffff 0 0**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [Cache Support for Streaming SIMD Extensions 2 Integer Operations](http://msdn.microsoft.com/zh-cn/a9c9b42f-de9e-4374-aeb6-5f65bfb669b6)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)