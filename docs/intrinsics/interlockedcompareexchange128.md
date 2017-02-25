---
title: "_InterlockedCompareExchange128 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedCompareExchange128_cpp"
  - "_InterlockedCompareExchange128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cmpxchg16b 指令"
  - "_InterlockedCompareExchange128 内部函数"
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _InterlockedCompareExchange128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 执行互锁的 128 位比较和交换。  
  
## 语法  
  
```  
unsigned char _InterlockedCompareExchange128(  
   __int64 volatile * Destination,  
   __int64 ExchangeHigh,  
   __int64 ExchangeLow,  
   __int64 * ComparandResult  
);  
```  
  
#### 参数  
 \[in, out\] `Destination`  
 对目标的指针，是 128 位域考虑的两个 64 位整数。  目标数据必须是对齐的 16 字节避免了通用保护错误。  
  
 \[in\] `ExchangeHigh`  
 可以交换使用该目标的高部分的 64 位整数。  
  
 \[in\] `ExchangeLow`  
 可以交换使用该目标的下半部分的 64 位整数。  
  
 \[in, out\] `ComparandResult`  
 对的指针两个 64 位整数 \(视为 128 位域\) 和目标进行比较。  在输出，则将复盖为目标的初始值。  
  
## 返回值  
 1，如果 128 位的相等比较为目标的初始值。  `ExchangeHigh` 和 `ExchangeLow` 复盖 128 位目标。  
  
 0，如果此比较线程不等于该目标的初始值。  为目标的值未更改，并且该比较数的值将复盖为目标的值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_InterlockedCompareExchange128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部生成`cmpxchg16b` 命令 \(与 `lock` 标题\) 执行被锁定的 128 位比较和交换。  AMD 64 位硬件的早期版本不支持该命令。  若要检查硬件为 `cmpxchg16b`命令支持，调用与 `InfoType=0x00000001 (standard function 1)`的 `__cpuid` 内部。  bit 的 13 `CPUInfo[2]`\(ECX\) 是 1，则命令支持。  
  
> [!NOTE]
>  `ComparandResult` 的值始终被复盖。  在 `lock` 命令后，此内部即时复制 `Destination` 的初始值为 `ComparandResult`。  因此， `ComparandResult` 和 `Destination` 应指向分隔内存位置避免意外行为。  
  
 虽然您可以为低级别线程同步使用 `_InterlockedCompareExchange128` ，则无需同步 128 位，则可以使用更小的同步功能 \(例如其他 `_InterlockedCompareExchange` 内部\)。  ，如果需要对 128 位值的基本访问内存，请使用 `_InterlockedCompareExchange128` 。  
  
 如果运行使用在硬件的固有不支持 `cmpxchg16b` 命令的代码，结果是不可预知的。  
  
 此实例仅可用作内部。  
  
## 示例  
 此示例使用 `_InterlockedCompareExchange128` 使用其所有单词的总和替换的高位字中。两个 64 位整数和递增低运行。  为 BigInt.Int 数组的访问是原子，但是，此示例使用单线程并忽略简要锁。  
  
```  
// cmpxchg16b.c  
// processor: x64  
// compile with: /EHsc /O2  
#include <stdio.h>  
#include <intrin.h>  
  
typedef struct _LARGE_INTEGER_128 {  
    __int64 Int[2];  
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;  
  
volatile LARGE_INTEGER_128 BigInt;  
  
// This AtomicOp() function atomically performs:  
//   BigInt.Int[1] += BigInt.Int[0]  
//   BigInt.Int[0] += 1  
void AtomicOp ()  
{  
    LARGE_INTEGER_128 Comparand;  
    Comparand.Int[0] = BigInt.Int[0];  
    Comparand.Int[1] = BigInt.Int[1];  
    do {  
        ; // nothing  
    } while (_InterlockedCompareExchange128(BigInt.Int,  
                                            Comparand.Int[0] + Comparand.Int[1],  
                                            Comparand.Int[0] + 1,  
                                            Comparand.Int) == 0);  
}  
  
// In a real application, several threads contend for the value  
// of BigInt.  
// Here we focus on the compare and exchange for simplicity.  
int main(void)  
{  
   BigInt.Int[1] = 23;  
   BigInt.Int[0] = 11;  
   AtomicOp();  
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",  
      BigInt.Int[1],BigInt.Int[0]);  
}  
```  
  
  **BigInt.Int \[1\] \= 34， BigInt.Int \[0\] \= 12**   
## 特定于 Microsoft 的结尾  
 由 Advanced Micro 设备，公司版权所有 2007。  保留所有权利。  重现经 Advanced Micro 设备授予，公司。  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_InterlockedCompareExchange Intrinsic Functions](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)