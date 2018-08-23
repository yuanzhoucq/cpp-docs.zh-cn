---
title: 'Mutex:: lock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 38bd11620f8d403bbd1667ab6fa4f3f827362c88
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600868"
---
# <a name="mutexlock-method"></a>Mutex::Lock 方法

等到当前对象或**互斥体**与指定句柄，互斥体或指定的超时间隔已过的版本关联的对象。

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

*毫秒*  
超时间隔（以毫秒为单位）。 默认值为 INFINITE，其表示将无限期地等待。

*h*  
句柄**互斥体**对象。

## <a name="return-value"></a>返回值

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅
[Mutex 类](../windows/mutex-class1.md)