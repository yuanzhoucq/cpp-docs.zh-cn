---
title: "__rdtscp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__rdtscp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rdtscp 内部函数"
  - "__rdtscp 内部函数"
  - "rdtscp 指令"
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __rdtscp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `rdtscp` 命令，编写 `TSC_AUX[31:0`out\] 内存，并返回 64 位时间戳计数器 \(`TSC)` 结果。  
  
## 语法  
  
```  
unsigned __int64 __rdtscp(  
   unsigned int * Aux  
);  
```  
  
#### 参数  
 \[out\] `Aux`  
 对于将包含有关各个计算机的注册 `TSC_AUX[31:0]`的目录位置的指针。  
  
## 返回值  
 64 位无符号整数滴答计数。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__rdtscp`|AMD NPT 系列 0Fh 或更高版本|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部生成 `rdtscp` 命令。  若要确定硬件为此命令支持，调用与 `InfoType=0x80000001` 的 `__cpuid`内部和校验位 27 `CPUInfo[3] (EDX)`。  此位否则为 1，则命令支持和 0。  如果运行使用在硬件的固有不支持 `rdtscp` 命令的代码，结果是不可预知的。  
  
> [!CAUTION]
>  不同 `rdtsc`， `rdtscp` 是序列化的命令;但是，编译器可以在该内部周围移动代码。  
  
 TSC 值的解释在硬件的此生成的与在 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]的早期版本。  请参见硬件准则有关更多信息。  
  
 值的含义。 `TSC_AUX[31:0]` 的取决于操作系统。  
  
## 示例  
  
```  
#include <intrin.h>   
#include <stdio.h>  
int main()   
{  
 unsigned __int64 i;  
 unsigned int ui;  
 i = __rdtscp(&ui);  
 printf_s("%I64d ticks\n", i);  
 printf_s("TSC_AUX was %x\n", ui);  
}  
```  
  
  **3363423610155519 滴答**  
**TSC\_AUX 为 0**   
## 特定于 Microsoft 的结尾  
 copyright 2007 年 Advanced Micro 设备，公司着。  保留所有权利。  重现经 Advanced Micro 设备授予，公司。  
  
## 请参阅  
 [\_\_rdtsc](../intrinsics/rdtsc.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)