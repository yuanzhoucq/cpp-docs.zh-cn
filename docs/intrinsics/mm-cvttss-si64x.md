---
title: "_mm_cvttss_si64x | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_cvttss_si64x"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mm_cvttss_si64x 内部函数"
  - "cvttss2si 指令"
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _mm_cvttss_si64x
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 发出转换的 x64 extended 版本具有截断单精度浮点数于 64 位整数 \(`cvttss2si`\) 命令。  
  
## 语法  
  
```  
__int64 _mm_cvttss_si64x(   
   __m128 value   
);  
```  
  
#### 参数  
 \[in\] `value`  
 包含单精度浮点值的 `__m128` 结构。  
  
## 返回值  
 第一个浮点值转换的结果到 64 位整数。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_mm_cvttss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 内部使用 `_mm_cvtss_si64x` 只是在不完全的转换截断到该零。  由于 `__m128` 结构表示 XMM 寄存器，生成的命令从个 XMM 寄存器将数据系统内存。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// _mm_cvttss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvttss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] = { 101.5, 200.75,  
                                          300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvttss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
  **101**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [\_\_m128](../cpp/m128.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)