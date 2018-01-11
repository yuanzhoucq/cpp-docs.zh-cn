---
title: "_ReadWriteBarrier |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _ReadWriteBarrier
dev_langs: C++
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2235c2089dd23a0572e960b995958c9e1740e108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier
**Microsoft 专用**  
  
 限制可重新排列调用点上的内存访问的编译器优化。  
  
> [!CAUTION]
>  已全部弃用且不应使用 `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 编译器内部函数和 `MemoryBarrier` 宏。 对于线程间通信使用机制例如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)和[std::atomic\<T >](../standard-library/atomic.md)，其定义中[c + + 标准库](../standard-library/cpp-standard-library-reference.md). 硬件访问，请使用[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)一起使用的编译器选项[易失性](../cpp/volatile-cpp.md)关键字。  
  
## <a name="syntax"></a>语法  
  
```  
void _ReadWriteBarrier(void);  
```  
  
## <a name="requirements"></a>惠?  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_ReadWriteBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 `_ReadWriteBarrier` 内部函数将限制可删除或重新排列调用点上的内存访问的编译器优化。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_ReadBarrier](../intrinsics/readbarrier.md)   
 [_WriteBarrier](../intrinsics/writebarrier.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [关键字](../cpp/keywords-cpp.md)