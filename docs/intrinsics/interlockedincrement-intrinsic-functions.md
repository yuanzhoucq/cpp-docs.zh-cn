---
title: _InterlockedIncrement 内部函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 900200eb1894a4f7065a008aeada9b90e71c6fcd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575783"
---
# <a name="interlockedincrement-intrinsic-functions"></a>_InterlockedIncrement 内部函数
**Microsoft 专用**  
  
 提供编译器内部函数支持 Win32 Windows SDK [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement)函数。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 [in, out] `lpAddend`  
 指向要递增的变量的指针。  
  
## <a name="return-value"></a>返回值  
 返回值是生成的递增值。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|Header|  
|---------------|------------------|------------|  
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86、 ARM、 x64|\<intrin.h>|  
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h>|  
  
## <a name="remarks"></a>备注  
 `_InterlockedIncrement` 存在几种变体，这些变体根据其涉及的数据类型和是否使用特定于处理器获取或发布语义而有所不同。  
  
 当 `_InterlockedIncrement` 函数对 32 位整数值操作时，`_InterlockedIncrement16` 对 16 位整数值操作且 `_InterlockedIncrement64` 可以对 64 位整数值操作。  
  
 ARM 平台上，如果需要（例如在临界区的起点和终点）获取和发布语义，可以使用带 `_acq` 和 `_rel` 后缀的函数。 带 `_nf`（“无围墙”）后缀的内部函数不能充当内存屏障。  
  
 由 `lpAddend` 参数指向的变量必须与 32 位边界对齐；否则，此函数在多处理器 x86 系统和任何非 x86 系统上将失效。 有关详细信息，请参阅[对齐](../cpp/align-cpp.md)。  
  
 Win32 函数在 `Wdm.h` 或 `Ntddk.h` 中声明。  
  
 这些例程只能用作内部函数。  
  
## <a name="example"></a>示例  
 有关如何使用的示例`_InterlockedIncrement`，请参阅[_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)