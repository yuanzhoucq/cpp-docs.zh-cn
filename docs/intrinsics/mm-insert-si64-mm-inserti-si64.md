---
title: "_mm_insert_si64, _mm_inserti_si64 | Microsoft Docs"
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
  - "_mm_inserti_si64"
  - "_mm_insert_si64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movsq 指令"
  - "_mm_insert_si64 intrinsic"
  - "_mm_inserti_si64 intrinsic"
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mm_insert_si64, _mm_inserti_si64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `insertq` 命令将从其第二个操作数对象插入位设置为其第一个操作数。  
  
## 语法  
  
```  
__m128i _mm_insert_si64(  
   __m128i Source1,  
   __m128i Source2  
);  
__m128i _mm_inserti_si64(  
   __m128i Source1,  
   __m128i Source2  
   int Length,  
   int Index  
);  
```  
  
#### 参数  
 \[in\]`Source1`  
 与输入数据的 128 位域在字段中插入其较低的 64 位。  
  
 \[in\]  `Source2`  
 与数据的 128 位域对其低位的插入。  对于 `_mm_insert_si64`，在其高位还包含字段描述符。  
  
 \[in\]  `Length`  
 指定字段的长度插入的整数常数。  
  
 \[in\]  `Index`  
 指定字段最低有效位索引要插入数据的整数常数。  
  
## 返回值  
 较低的 64 位包含原始低 64 位与指定的位域的 `Source1` 的 128 位域中低位 `Source2`替换。  返回值的上限 64 位未定义。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_mm_insert_si64`|SSE4a|  
|`_mm_inserti_si64`|SSE4a|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部生成 `insertq` 命令将从 `Source2` 插入位设置为 `Source1`。  具有固有的两个版本: `_mm_inserti_si64`，这是立即版本，并且， `_mm_insert_si64` 非立即一个。  每个版本从 Source2 和插入提取特定长度的位域到 Source1 中。  提取的位为最低有效位 Source2。  字段这些位要插入的 Source1 由长度及其最低有效位索引定义。  长度和索引值执行 mod 64，从而 \-1 和 127 被解释为 63。  如果总和 \(减小\) 超过 64 位了索引和 \(降低\) 字段长度，结果是未定义的。  零值字段长度的被解释为 64。  如果字段长度和个索引是两个零， 63:0 位 `Source2` 插入 `Source1`。  如果字段长度为零，但个索引是非零，则结果是未定义的。  
  
 在对 \_mm\_insert\_si64 的调用，字段长度在 Source2 位 77:72 和索引包含在位 69:64。  
  
 如果您调用了编译器无法确定是整数常数参数的 `_mm_inserti_si64`，编译器生成代码打包这些值到个 XMM 寄存器和调用 `_mm_insert_si64`。  
  
 若要确定硬件为 `insertq` 命令支持调用与 `InfoType=0x80000001` 的 `__cpuid` 内部和校验位 6 `CPUInfo[2] (ECX)`。  此位会为 1，则命令支持和 0。  如果运行使用在硬件的固有不支持 `insertq` 命令的代码，结果是不可预知的。  
  
## 示例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source1, source2, source3, result1, result2, result3;  
  
int  
main()  
{  
  
    __int64 mask;  
  
    source1.ui64[0] = 0xffffffffffffffffll;  
    source2.ui64[0] = 0xfedcba9876543210ll;  
    source2.ui64[1] = 0xc10;  
    source3.ui64[0] = source2.ui64[0];  
  
    result1.m = _mm_insert_si64 (source1.m, source2.m);  
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);  
    mask = 0xffff << 12;  
    mask = ~mask;  
    result3.ui64[0] = (source1.ui64[0] & mask) |  
                      ((source2.ui64[0] & 0xffff) << 12);  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
  
}  
```  
  
  **result1 \= 0xfffffffff3210fff**  
**result2 \= 0xfffffffff3210fff**  
**result3 \= 0xfffffffff3210fff**   
## 特定于 Microsoft 的结尾  
 copyright 2007 年 Advanced Micro 设备，公司着。  保留所有权利。  重现经 Advanced Micro 设备授予，公司。  
  
## 请参阅  
 [\_mm\_extract\_si64、\_mm\_extracti\_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)