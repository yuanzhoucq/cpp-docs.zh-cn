---
title: "_mm_cvtss_si64x | Microsoft Docs"
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
  - "_mm_cvtss_si64x"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cvtss2si 指令"
  - "_mm_cvtss_si64x 指令"
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mm_cvtss_si64x
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成转换标量单倍精度浮点数的 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] extended 版本为 64 位整数 \(`cvtss2si`\) 命令。  
  
## 语法  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### 参数  
 \[in\] `value`  
 包含浮动 point 值的 `__m128` 结构。  
  
## 返回值  
 一个 64 位整数，第一个浮点值转换的结果为整数。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_mm_cvtss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 结构值的第一个元素转换为整数并返回。  在 MXCSR 的舍入的控件位用于确定该轮的行为。  默认舍入模式是在周围最靠近，舍入为偶数，如果该小数部分为 0.5。  由于 `__m128` 结构表示 XMM 寄存器，此内部来自个 XMM 寄存器和写入的值到系统内存。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// _mm_cvtss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] =  
                           { 101.25, 200.75, 300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvtss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
  **101**   
## 关闭 Microsoft 特定  
  
## 请参阅  
 [\_\_m128d](../cpp/m128d.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)