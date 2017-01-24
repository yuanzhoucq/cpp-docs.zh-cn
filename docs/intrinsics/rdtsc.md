---
title: "__rdtsc | Microsoft Docs"
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
  - "__rdtsc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__rdtsc 内部函数"
  - "rdtsc 指令"
  - "读取时间戳计数器指令"
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __rdtsc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `rdtsc` 命令，返回处理器时间戳。  处理器时间戳记录时钟周期数从最后一个默认值。  
  
## 语法  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## 返回值  
 表示滴答计数的 64 位无符号整数。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__rdtsc`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例仅可用作内部。  
  
 TSC 值的解释在硬件的此生成的与在 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]的早期版本。  请参见硬件准则有关更多信息。  
  
## 示例  
  
```  
// rdtsc.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__rdtsc)  
  
int main()  
{  
    unsigned __int64 i;  
    i = __rdtsc();  
    printf_s("%I64d ticks\n", i);  
}  
```  
  
  **3363423610155519 滴答**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)