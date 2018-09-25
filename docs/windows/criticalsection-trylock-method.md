---
title: 'Criticalsection:: Trylock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44b4e251898ef6386d0642582af2c00881f7a181
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408578"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock 方法

尝试进入关键节而不会阻塞。 如果调用成功，调用线程将取得所有权的关键部分。

## <a name="syntax"></a>语法

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>参数

*cs*<br/>
用户指定的关键部分对象。

## <a name="return-value"></a>返回值

如果成功进入关键节一个非零值或当前线程已拥有关键部分。 如果另一个线程已拥有关键部分，则为零。

## <a name="remarks"></a>备注

第一个**TryLock**函数影响当前关键部分对象。 第二个**TryLock**函数影响用户指定的关键部分。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[CriticalSection 类](../windows/criticalsection-class.md)