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
ms.openlocfilehash: 11719576c9fc7b23f4cd318ee1b3ed9ca3f5edaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360730"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits 结构

定义`Semaphore`对象的常见特征。

## <a name="syntax"></a>语法

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

名称                               | 说明
---------------------------------- | --------------------------------------
[信号量：解锁](#unlock) | 释放对共享资源的控制。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：：处理特征

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a>信号量：解锁

释放对共享资源的控制。

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>参数

*H*<br/>
处理`Semaphore`对象。

### <a name="remarks"></a>备注

如果解锁操作不成功，`Unlock()`则发出指示故障原因的错误。
