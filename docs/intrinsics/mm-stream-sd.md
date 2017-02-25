---
title: "_mm_stream_sd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_stream_sd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mm_stream_sd 内部函数"
  - "movntsd 指令"
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _mm_stream_sd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 对内存位置编写 64 位数据没有污染缓存。  
  
## 语法  
  
```  
void _mm_stream_sd(  
   double * Dest,  
   __m128d Source  
);  
```  
  
#### 参数  
 \[out\]`Dest`  
 对源数据将写入的位置的指针。  
  
 \[in\] `Source`  
 包含 `double` 值为 128 位值将写入在其底部 64 位。  
  
## 返回值  
 无。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_mm_stream_sd`|SSE4a|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部生成 `movntsd`命令。  若要确定硬件为此命令支持，调用与 `InfoType=0x80000001` 的 `__cpuid` 内部和校验位 6 `CPUInfo[2] (ECX)`。  此位否则为 1，则硬件支持此命令和 0。  
  
 如果运行使用在硬件的 `_mm_stream_sd` 内部不支持 `movntsd` 命令的代码，结果是不可预知的。  
  
## 示例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
int main()  
{  
    __m128d vals;  
    double d[2];  
  
    d[0] = -1.;  
    d[1] = -2.;  
    vals.m128d_f64[0] = 0.;  
    vals.m128d_f64[1] = 1.;  
    _mm_stream_sd(&d[1], vals);  
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;  
}  
  
```  
  
  **d\] \[0 \= \-1， d\] \[1 \= 1**   
## 特定于 Microsoft 的结尾  
 copyright 2007 年 Advanced Micro 设备，公司着。  保留所有权利。  重现经 Advanced Micro 设备授予，公司。  
  
## 请参阅  
 [\_mm\_stream\_ss](../intrinsics/mm-stream-ss.md)   
 [\_mm\_store\_sd](http://msdn.microsoft.com/zh-cn/8e672d0d-0a96-45b9-a783-392a2457de42)   
 [\_mm\_sfence](http://msdn.microsoft.com/zh-cn/b6c0d18e-3628-4318-826b-45f66782e870)   
 [Streaming SIMD Extensions that Support the Cache](http://msdn.microsoft.com/zh-cn/8f03493a-d5f5-4457-892e-0b6540494872)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)