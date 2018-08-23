---
title: 'Criticalsection:: Lock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4fedde29441c9c14b68dec5cff998be57d216e29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607655"
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock 方法

等待指定关键部分对象的所有权。 此函数将在授予调用线程所有权时返回。

## <a name="syntax"></a>语法

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>参数

*cs*  
用户指定的关键部分对象。

## <a name="return-value"></a>返回值

可用于取消锁定当前关键部分的锁定对象。

## <a name="remarks"></a>备注

第一个**锁**函数影响当前关键部分对象。 第二个**锁**函数影响用户指定的关键部分。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[CriticalSection 类](../windows/criticalsection-class.md)