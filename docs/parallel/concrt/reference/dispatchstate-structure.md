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
ms.openlocfilehash: 2c4103f89f7fc74c5368bafac3c82685ff9b6e03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372700"
---
# <a name="dispatchstate-structure"></a>DispatchState 结构

`DispatchState` 结构用于将状态传输给 `IExecutionContext::Dispatch` 方法。 它描述了在 `IExecutionContext` 接口上调用 `Dispatch` 方法的情形。

## <a name="syntax"></a>语法

```cpp
struct DispatchState;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[调度状态：:D](#ctor)|构造新的 `DispatchState` 对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[调度状态：：m_dispatchStateSize](#m_dispatchstatesize)|此结构的大小，用于版本控制。|
|[调度状态：：m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|告知此上下文是否已输入方法，`Dispatch`因为以前的上下文异步阻止。 这仅在 UMS 计划上下文中使用，并设置为所有其他执行上下文的值`0`。|
|[调度状态：：m_reserved](#m_reserved)|保留供将来传递信息的位。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`DispatchState`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="dispatchstatedispatchstate-constructor"></a><a name="ctor"></a>调度状态：:Dispatch 状态构造函数

构造新的 `DispatchState` 对象。

```cpp
DispatchState();
```

## <a name="dispatchstatem_dispatchstatesize-data-member"></a><a name="m_dispatchstatesize"></a>调度状态：：m_dispatchStateSize 数据成员

此结构的大小，用于版本控制。

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="dispatchstatem_fispreviouscontextasynchronouslyblocked-data-member"></a><a name="m_fispreviouscontextasynchronouslyblocked"></a>调度状态：：m_fIsPreviousContextAsynchronouslyBlocked数据成员

告知此上下文是否已输入方法，`Dispatch`因为以前的上下文异步阻止。 这仅在 UMS 计划上下文中使用，并设置为所有其他执行上下文的值`0`。

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="dispatchstatem_reserved-data-member"></a><a name="m_reserved"></a>调度状态：：m_reserved数据成员

保留供将来传递信息的位。

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)
