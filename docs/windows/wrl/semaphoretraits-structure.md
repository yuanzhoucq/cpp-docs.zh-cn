---
title: SemaphoreTraits 结构
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: e7bd2e5d0993c8e4be7223d98ffb1dbec14cbb74
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335900"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits 结构

定义常见特征`Semaphore`对象。

## <a name="syntax"></a>语法

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

名称                               | 描述
---------------------------------- | --------------------------------------
[SemaphoreTraits::Unlock](#unlock) | 版本控制共享资源。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>SemaphoreTraits::Unlock

版本控制共享资源。

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>参数

*h*<br/>
句柄`Semaphore`对象。

### <a name="remarks"></a>备注

如果解锁操作不成功，`Unlock()`发出一个错误，指示失败的原因。
