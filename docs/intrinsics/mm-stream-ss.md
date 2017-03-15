---
title: "_mm_stream_ss | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_stream_ss"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movntss 指令"
  - "_mm_stream_ss 指令"
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _mm_stream_ss
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 对内存位置编写 32 位数据没有污染缓存。  
  
## 语法  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### 参数  
 \[out\] `Dest`  
 对源数据写入的位置的指针。  
  
 \[in\] `Source`  
 包含在其底部 32 位将写入的值。 `float` 的 128 位数字。  
  
## 返回值  
 无。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_mm_stream_ss`|SSE4a|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部生成 `movntss`命令。  若要确定硬件为此命令支持，调用与 `InfoType=0x80000001`的 `__cpuid` 内部和校验位 6 `CPUInfo[2] (ECX)`。  当该指令受支持时，此位为 1，否则为 0。  
  
 如果运行使用在硬件的 `_mm_stream_ss` 内部不支持 `movntss` 命令的代码，结果是不可预知的。  
  
## 示例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
int main()  
{  
    __m128 vals;  
    float f[4];  
  
    f[0] = -1.;  
    f[1] = -2.;  
    f[2] = -3.;  
    f[3] = -4.;  
    vals.m128_f32[0] = 0.;  
    vals.m128_f32[1] = 1.;  
    vals.m128_f32[2] = 2.;  
    vals.m128_f32[3] = 3.;  
    _mm_stream_ss(&f[3], vals);  
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;  
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;  
}  
  
```  
  
  **f \[0\] \= \-1， f \[1\] \= \-2**  
**f \[2\] \= \-3， f \[3\] \= 3**   
## 特定于 Microsoft 的结尾  
 copyright 2007 年 Advanced Micro 设备，公司着。  保留所有权利。  重现经 Advanced Micro 设备授予，公司。  
  
## 请参阅  
 [\_mm\_stream\_sd](../intrinsics/mm-stream-sd.md)   
 [\_mm\_stream\_ps](http://msdn.microsoft.com/zh-cn/f7af2f19-c0d4-43c6-b5f6-a658d2b1d869)   
 [\_mm\_store\_ss](http://msdn.microsoft.com/zh-cn/dfeeea35-8faf-4f54-8a9e-6723e226fb08)   
 [\_mm\_sfence](http://msdn.microsoft.com/zh-cn/b6c0d18e-3628-4318-826b-45f66782e870)   
 [Streaming SIMD Extensions that Support the Cache](http://msdn.microsoft.com/zh-cn/8f03493a-d5f5-4457-892e-0b6540494872)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)