---
title: "_mm_extract_si64、_mm_extracti_si64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_extracti_si64"
  - "_mm_extract_si64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extrq 指令"
  - "_mm_extracti_si64 内部函数"
  - "_mm_extract_si64 内部函数"
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _mm_extract_si64、_mm_extracti_si64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `extrq` 命令从低 64 位其第一个参数提取指定的位。  
  
## 语法  
  
```  
__m128i _mm_extract_si64(  
   __m128i Source,  
   __m128i Descriptor  
);  
__m128i _mm_extracti_si64(  
   __m128i Source,  
   int Length,  
   int Index  
);  
```  
  
#### 参数  
 \[in\]`Source`  
 与输入数据的 128 位域在其较低的 64 位。  
  
 \[in\]  `Descriptor`  
 描述位域提取的 128 位域。  
  
 \[in\]  `Length`  
 指定字段的长度提取的整数。  
  
 \[in\]  `Index`  
 指定字段提取的整数索引  
  
## 返回值  
 与提取字段的 128 位域在其最低有效位。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_mm_extract_si64`|SSE4a|  
|`_mm_extracti_si64`|SSE4a|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部生成 `extrq` 命令从 `Source`提取位。具有固有的两个版本: `_mm_extracti_si64` 为立即版本，并且， `_mm_extract_si64` 非立即一个。  每个版本从位域由其长度及其最低有效位索引定义的 `Source` 提取。  长度和索引值执行 mod 64，从而 \-1 和 127 被解释为 63。  如果 \(减少的索引\) 和 \(降低\) 字段长度之和大于 64，结果是未定义的。  零值字段长度的被解释为 64。  如果字段长度和个索引是两个零， 63:0 位 `Source` 中提取。  如果字段长度为零，但个索引是非零，则结果是未定义的。  
  
 在对 \_mm\_extract\_si64 的调用， `Descriptor` 在 13:8 位和 5:0 位在中提取数据的字段长包含索引。  
  
 如果您调用了编译器无法确定是整数常数编译器参数的 `_mm_extracti_si64` 生成代码打包这些值到个 XMM 寄存器 \(`Descriptor`\) 和调用 `_mm_extract_si64`。  
  
 若要确定硬件为 `extrq` 命令支持，调用与 `InfoType=0x80000001` 的 `__cpuid` 内部和校验位 6 `CPUInfo[2] (ECX)`。  此位会为 1，则命令支持和 0。  如果运行使用此内部硬件不支持 `extrq` 命令的代码，结果是不可预知的。  
  
## 示例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source, descriptor, result1, result2, result3;  
  
int  
main()  
{  
    source.ui64[0] =     0xfedcba9876543210ll;  
    descriptor.ui64[0] = 0x0000000000000b1bll;  
  
    result1.m = _mm_extract_si64 (source.m, descriptor.m);  
    result2.m = _mm_extracti_si64(source.m, 27, 11);  
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
}  
```  
  
  **result1 \= 0x30eca86**  
**result2 \= 0x30eca86**  
**result3 \= 0x30eca86**   
## 特定于 Microsoft 的结尾  
 copyright 2007 年 Advanced Micro 设备，公司着。  保留所有权利。  重现经 Advanced Micro 设备授予，公司。  
  
## 请参阅  
 [\_mm\_insert\_si64, \_mm\_inserti\_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)