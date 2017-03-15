---
title: "_InterlockedAdd 内部函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedAdd64_acq_cpp"
  - "_InterlockedAdd64_acq"
  - "_InterlockedAdd_acq"
  - "_InterlockedAdd_nf"
  - "_InterlockedAdd64_rel"
  - "_InterlockedAdd64"
  - "_InterlockedAdd_cpp"
  - "_InterlockedAdd_rel_cpp"
  - "_InterlockedAdd_rel"
  - "_InterlockedAdd64_rel_cpp"
  - "_InterlockedAdd64_cpp"
  - "_InterlockedAdd_acq_cpp"
  - "_InterlockedAdd64_nf"
  - "_InterlockedAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedAdd 内部函数"
  - "_InterlockedAdd_acq 内部函数"
  - "_InterlockedAdd_nf 内部函数"
  - "_InterlockedAdd_rel 内部函数"
  - "_InterlockedAdd64 内部函数"
  - "_InterlockedAdd64_acq 内部函数"
  - "_InterlockedAdd64_nf 内部函数"
  - "_InterlockedAdd64_rel 内部函数"
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _InterlockedAdd 内部函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 当多线程拥有对共享变量的访问权限时，执行原子加法可确保成功完成操作。  
  
## 语法  
  
```  
long _InterlockedAdd(    long volatile * Addend,    long Value ); long _InterlockedAdd_acq(    long volatile * Addend,    long Value ); long _InterlockedAdd_nf(    long volatile * Addend,    long Value ); long _InterlockedAdd_rel(    long volatile * Addend,    long Value ); __int64 _InterlockedAdd64(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_acq(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_nf (    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_rel(    __int64 volatile * Addend,    __int64 Value );  
```  
  
#### 参数  
 \[in, out\] `Addend`  
 指向要相加的整数的指针；由加法结果代替。  
  
 \[in\] `Value`  
 要相加的值。  
  
## 返回值  
 两个函数都将返回加法结果。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`_InterlockedAdd`|ARM|  
|`_InterlockedAdd_acq`|ARM|  
|`_InterlockedAdd_nf`|ARM|  
|`_InterlockedAdd_rel`|ARM|  
|`_InterlockedAdd64`|ARM|  
|`_InterlockedAdd64_acq`|ARM|  
|`_InterlockedAdd64_nf`|ARM|  
|`_InterlockedAdd64_rel`|ARM|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 带 `_acq` 或 `_rel` 后缀的这些版本的函数可在获取或发布语义后执行互锁加法。  获取语义意思是，在任何后续内存进行读取和写入之前，所有线程和处理器均能看见运算结果。  进入临界区时，获取十分有用。  发布语义意思是，在运算结果自己显示出来之前，将强制所有内存的读取和写入对所有线程和处理器可见。  离开临界区时，发布十分有用。  带 `_nf`（“无围墙”）后缀的内部函数不能充当内存屏障。  
  
 这些例程只能用作内部函数。  
  
## 示例  
  
```  
// interlockedadd.cpp  
// Compile with: /Oi /EHsc  
// processor: ARM  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedAdd)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FF0000;  
        long retval;  
        retval = _InterlockedAdd(&data1, data2);  
        printf("0x%x 0x%x 0x%x", data1, data2, retval);  
}  
```  
  
## 输出  
  
```  
0xffffff00 0xff0000 0xffffff00  
```  
  
## 示例  
  
```  
// interlockedadd64.cpp  
// compile with: /Oi /EHsc  
// processor: ARM  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_InterlockedAdd64)  
  
int main()  
{  
        __int64 data1 = 0x0000FF0000000000;  
        __int64 data2 = 0x00FF0000FFFFFFFF;  
        __int64 retval;  
        cout << hex << data1 << " + " << data2 << " = " ;  
        retval = _InterlockedAdd64(&data1, data2);  
        cout << data1 << endl;  
        cout << "Return value: " << retval << endl;  
}  
```  
  
## 输出  
  
```  
ff0000000000 + ff0000ffffffff = ffff00ffffffff  
Return value: ffff00ffffffff  
```  
  
### 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)