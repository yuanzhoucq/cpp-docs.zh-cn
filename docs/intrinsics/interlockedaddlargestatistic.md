---
title: _InterlockedAddLargeStatistic
ms.date: 11/04/2016
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: 6f9d599a8d7668c6c8a37846275e8338002589d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349483"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft 专用**

执行互锁的加法中的第一个操作数是一个 64 位值。

## <a name="syntax"></a>语法

```
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

#### <a name="parameters"></a>参数

*加数*<br/>
[in、 out]添加操作的第一个操作数指向的指针。 相加的结果将替换为指向的值。

*值*<br/>
[in]第二个操作数;要添加到第一个操作数的值。

## <a name="return-value"></a>返回值

第二个操作数的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数不是原子因为它实现两个独立的锁定的说明。 另一个线程上执行过程中发生此内部函数的原子 64 位读取可能导致所读取的不一致值。

此函数的行为作为读写屏障。 有关详细信息，请参阅[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)