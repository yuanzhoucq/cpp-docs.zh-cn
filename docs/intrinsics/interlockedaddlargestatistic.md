---
title: _InterlockedAddLargeStatistic |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 602cfb415c17c9e57d9fc1e932777cd1929e5f40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331392"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic
**Microsoft 专用**  
  
 执行互锁的加法在其中第一个操作数是一个 64 位值。  
  
## <a name="syntax"></a>语法  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in, out] `Addend`  
 指向添加操作的第一个操作数的指针。 指向的值替换为添加的结果。  
  
 [in] `Value`  
 第二个操作数;要添加到第一个操作数的值。  
  
## <a name="return-value"></a>返回值  
 第二个操作数的值。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此内部函数不是原子因为它实现两个独立的锁定的说明。 在另一个线程上执行过程中发生此内部函数的原子 64 位读取可能导致不一致所读取的值。  
  
 此函数的行为方式如读写屏障。 有关详细信息，请参阅[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)