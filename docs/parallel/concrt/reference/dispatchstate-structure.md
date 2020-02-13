---
title: DispatchState 结构
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: 69e00893373ccca6e2ed676fbb7f5a109c49efdf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143048"
---
# <a name="dispatchstate-structure"></a>DispatchState 结构

`DispatchState` 结构用于将状态传输给 `IExecutionContext::Dispatch` 方法。 它描述了在 `Dispatch` 接口上调用 `IExecutionContext` 方法的情形。

## <a name="syntax"></a>语法

```cpp
struct DispatchState;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[DispatchState：:D ispatchState](#ctor)|构造新的 `DispatchState` 对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[DispatchState：： m_dispatchStateSize](#m_dispatchstatesize)|此结构的大小，用于版本控制。|
|[DispatchState：： m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|指示此上下文是否已进入 `Dispatch` 方法，因为以前的上下文已异步阻止。 这仅用于 UMS 计划上下文，并设置为对所有其他执行上下文 `0` 的值。|
|[DispatchState：： m_reserved](#m_reserved)|保留以供将来信息通过的 Bits。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`DispatchState`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="ctor"></a>DispatchState：:D ispatchState 构造函数

构造新的 `DispatchState` 对象。

```cpp
DispatchState();
```

## <a name="m_dispatchstatesize"></a>DispatchState：： m_dispatchStateSize 数据成员

此结构的大小，用于版本控制。

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="m_fispreviouscontextasynchronouslyblocked"></a>DispatchState：： m_fIsPreviousContextAsynchronouslyBlocked 数据成员

指示此上下文是否已进入 `Dispatch` 方法，因为以前的上下文已异步阻止。 这仅用于 UMS 计划上下文，并设置为对所有其他执行上下文 `0` 的值。

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="m_reserved"></a>DispatchState：： m_reserved 数据成员

保留以供将来信息通过的 Bits。

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
