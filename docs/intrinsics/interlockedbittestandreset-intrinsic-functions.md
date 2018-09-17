---
title: _interlockedbittestandreset 内部函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _interlockedbittestandreset_rel
- _interlockedbittestandreset64
- _interlockedbittestandreset64_HLERelease
- _interlockedbittestandreset_HLERelease
- _interlockedbittestandreset_HLEAcquire
- _interlockedbittestandreset_acq
- _interlockedbittestandreset_cpp
- _interlockedbittestandreset_nf
- _interlockedbittestandreset64_cpp
- _interlockedbittestandreset64_HLEAcquire
- _interlockedbittestandreset
dev_langs:
- C++
helpviewer_keywords:
- lock_btr instruction
- _interlockedbittestandreset64 intrinsic
- _interlockedbittestandreset intrinsic
ms.assetid: 9bbb1442-f2e9-4dc2-b0da-97f3de3493b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12935c6a735d72bb1eb25627c78d69f362073a90
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724368"
---
# <a name="interlockedbittestandreset-intrinsic-functions"></a>_interlockedbittestandreset 内部函数
**Microsoft 专用**  
  
 生成一个指令，该指令将地址 `b` 的位 `a` 设置为零并返回其原始值。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char _interlockedbittestandreset(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_acq(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_HLEAcquire(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_HLERelease(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_nf(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_rel(  
   long *a,  
   long b  
);   
unsigned char _interlockedbittestandreset64(  
   __int64 *a,  
   __int64 b  
);   
unsigned char _interlockedbittestandreset64_HLEAcquire(  
   __int64 *a,  
   __int64 b  
);  
unsigned char _interlockedbittestandreset64_HLERelease(  
   __int64 *a,  
   __int64 b  
);  
```  
  
#### <a name="parameters"></a>参数  
*a*<br/>
[in]指向要检查的内存的指针。  
  
*b*<br/>
[in]要测试的位位置。  
  
## <a name="return-value"></a>返回值  
 由 `b` 指定的位置上的位的原始值。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|Header|  
|---------------|------------------|------------|  
|`_interlockedbittestandreset`|x86、 ARM、 x64|\<intrin.h>|  
|`_interlockedbittestandreset_acq`, `_interlockedbittestandreset_nf`, `_interlockedbittestandreset_rel`|ARM|\<intrin.h>|  
|`_interlockedbittestandreset_HLEAcquire`, `_interlockedbittestandreset_HLERelease`|x86、x64|\<immintrin.h>|  
|`_interlockedbittestandreset64`|X64|\<intrin.h>|  
|`_interlockedbittestandreset64_HLEAcquire`, `_interlockedbittestandreset64_HLERelease`|X64|\<immintrin.h>|  
  
## <a name="remarks"></a>备注  
 在 x86 和 x64 处理器上，这些内部函数使用`lock btr`指令，读取，并在原子操作中设置为零的指定的位。  
  
 在 ARM 处理器上，使用带 `_acq` 和 `_rel` 后缀的内部函数（例如在临界区的起点和结尾处）获取和发布语义。 带 `_nf`（“无围墙”）后缀的 ARM 内部函数不能充当内存屏障。  
  
 在支持硬件锁省略 (HLE) 指令的 Intel 处理器上，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一条发送到处理器的提示，可通过消除硬件中的锁写步骤加快速度。 如果在不支持 HLE 的处理器上调用这些函数，则忽略此提示。  
  
 这些例程只能用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)