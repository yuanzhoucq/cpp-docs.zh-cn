---
title: "_mm_cvtsi64x_ss | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_cvtsi64x_ss"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cvtsi2ss 指令"
  - "_mm_cvtsi64x_ss 内部函数"
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _mm_cvtsi64x_ss
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成转换 64 位整数的 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] extended 版本为标量单精度浮点值 \(`cvtsi2ss`\) 命令。  
  
## 语法  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### 参数  
 \[in\] `a`  
 包含四个单精度浮点值的 `__m128` 结构。  
  
 \[in\] `b`  
 要转换的 64 位整数转换为浮点值。  
  
## 返回值  
 第一个浮点值是转换的结果的 `__m128` 结构。  其他三个值从 `a`原样复制。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_mm_cvtsi64x_ss`|x64|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `__m128` 结构表示一个 XMM 寄存器，因此，此内部允许从系统内存的值 `b` 将 XMM 寄存器。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
  **54.000000 0.000000 0.000000 0.000000**   
## 关闭 Microsoft 特定  
  
## 请参阅  
 [\_\_m128](../cpp/m128.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)