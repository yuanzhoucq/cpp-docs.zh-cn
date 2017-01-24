---
title: "_InterlockedIncrement 内部函数 | Microsoft Docs"
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
  - "_InterlockedIncrement_acq"
  - "_InterlockedIncrement16_rel_cpp"
  - "_InterlockedIncrement16_cpp"
  - "_InterlockedIncrement64_rel"
  - "_InterlockedIncrement_rel"
  - "_InterlockedIncrement64_nf"
  - "_InterlockedIncrement16_acq_cpp"
  - "_InterlockedIncrement_rel_cpp"
  - "_InterlockedIncrement64"
  - "_InterlockedIncrement64_rel_cpp"
  - "_InterlockedIncrement16_nf"
  - "_InterlockedIncrement16_rel"
  - "_InterlockedIncrement16_acq"
  - "_InterlockedIncrement_nf"
  - "_InterlockedIncrement_acq_cpp"
  - "_InterlockedIncrement64_cpp"
  - "_InterlockedIncrement64_acq_cpp"
  - "_InterlockedIncrement"
  - "_InterlockedIncrement_cpp"
  - "_InterlockedIncrement64_acq"
  - "_InterlockedIncrement16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedIncrement 内部函数"
  - "_InterlockedIncrement_acq 内部函数"
  - "_InterlockedIncrement_nf 内部函数"
  - "_InterlockedIncrement_rel 内部函数"
  - "_InterlockedIncrement16 内部函数"
  - "_InterlockedIncrement16_acq 内部函数"
  - "_InterlockedIncrement16_nf 内部函数"
  - "_InterlockedIncrement16_rel 内部函数"
  - "_InterlockedIncrement64 内部函数"
  - "_InterlockedIncrement64_acq 内部函数"
  - "_InterlockedIncrement64_nf 内部函数"
  - "_InterlockedIncrement64_rel 内部函数"
  - "InterlockedIncrement 内部函数"
  - "InterlockedIncrement_acq 内部函数"
  - "InterlockedIncrement_rel 内部函数"
  - "InterlockedIncrement16 内部函数"
  - "InterlockedIncrement64 内部函数"
  - "InterlockedIncrement64_acq 内部函数"
  - "InterlockedIncrement64_rel 内部函数"
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedIncrement 内部函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 为 Win32 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [InterlockedIncrement](http://msdn.microsoft.com/library/ms683614.aspx) 函数提供编译器内部支持。  
  
## 语法  
  
```  
long _InterlockedIncrement(  
   long * lpAddend  
);  
long _InterlockedIncrement_acq(  
   long * lpAddend  
);  
long _InterlockedIncrement_rel(  
   long * lpAddend  
);  
long _InterlockedIncrement_nf(  
   long * lpAddend  
);  
short _InterlockedIncrement16(  
   short * lpAddend  
);  
short _InterlockedIncrement16_acq(  
   short * lpAddend  
);  
short _InterlockedIncrement16_rel(  
   short * lpAddend  
);  
short _InterlockedIncrement16_nf (  
   short * lpAddend  
);  
__int64 _InterlockedIncrement64(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_acq(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_rel(  
   __int64 * lpAddend  
);   
__int64 _InterlockedIncrement64_nf(  
   __int64 * lpAddend  
);  
```  
  
#### 参数  
 \[in, out\] `lpAddend`  
 指向要递增的变量的指针。  
  
## 返回值  
 返回值是生成的递增值。  
  
## 要求  
  
|内部函数|体系结构|标头|  
|----------|----------|--------|  
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h\>|  
  
## 备注  
 `_InterlockedIncrement` 存在几种变体，这些变体根据其涉及的数据类型和是否使用特定于处理器获取或发布语义而有所不同。  
  
 当 `_InterlockedIncrement` 函数对 32 位整数值操作时，`_InterlockedIncrement16` 对 16 位整数值操作且 `_InterlockedIncrement64` 可以对 64 位整数值操作。  
  
 ARM 平台上，如果需要（例如在临界区的起点和终点）获取和发布语义，可以使用带 `_acq` 和 `_rel` 后缀的函数。  带 `_nf`（“无围墙”）后缀的内部函数不能充当内存屏障。  
  
 由 `lpAddend` 参数指向的变量必须与 32 位边界对齐；否则，此函数在多处理器 x86 系统和任何非 x86 系统上将失效。  有关更多信息，请参阅[对齐](../cpp/align-cpp.md)。  
  
 Win32 函数在 `Wdm.h` 或 `Ntddk.h` 中声明。  
  
 这些例程只能用作内部函数。  
  
## 示例  
 有关如何使用 `_InterlockedIncrement` 的示例，请参阅 [\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)