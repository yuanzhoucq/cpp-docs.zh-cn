---
title: 'Semaphore:: lock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2083992bcb444a10b495b7007c698499f9cd9628
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419160"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock 方法

等到当前对象或**信号量**对象与指定句柄处于已发出信号状态或指定的超时间隔已过。

## <a name="syntax"></a>语法

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>参数

*毫秒*<br/>
超时间隔（以毫秒为单位）。 默认值为 INFINITE，其表示将无限期地等待。

*h*<br/>
句柄**信号量**对象。

## <a name="return-value"></a>返回值

一个 `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Semaphore 类](../windows/semaphore-class.md)