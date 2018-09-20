---
title: 'Srwlock:: Trylockshared 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs:
- C++
helpviewer_keywords:
- TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 985629f224f199d1b1f095847e64cc67fa5a97f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388455"
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared 方法

尝试获取**SRWLock**对象中的当前或指定的共享模式**SRWLock**对象。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>参数

*lock*<br/>
指向**SRWLock**对象。

## <a name="return-value"></a>返回值

如果成功， **SRWLock**共享的模式和调用线程中的对象采用锁的所有权。 否则为**SRWLock**对象，其状态为无效。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[SRWLock 类](../windows/srwlock-class.md)