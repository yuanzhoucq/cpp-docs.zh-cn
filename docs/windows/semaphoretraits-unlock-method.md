---
title: 'Semaphoretraits:: Unlock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e993c58ea6fc84e0b4001b488632858e5251d67b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583966"
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock 方法

版本控制共享资源。

## <a name="syntax"></a>语法

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>参数

*h*  
句柄**信号量**对象。

## <a name="remarks"></a>备注

如果解锁操作不成功， **Unlock()** 发出一个错误，指示失败的原因。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>请参阅

[SemaphoreTraits 结构](../windows/semaphoretraits-structure.md)