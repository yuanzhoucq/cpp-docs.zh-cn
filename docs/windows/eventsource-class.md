---
title: EventSource 类
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: e9070fe756410e3e1bb1e5840eb3f06e29c2f46b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561273"
---
# <a name="eventsource-class"></a>EventSource 类

表示非敏捷事件。 `EventSource` 成员函数将添加、删除和调用事件处理程序。 对于 agile 事件，使用[AgileEventSource](agileeventsource-class.md)。

## <a name="syntax"></a>语法

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>参数

*TDelegateInterface*<br/>
一个委托，表示一个事件处理程序接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

| 名称                                     | 描述                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [Eventsource:: Eventsource](#eventsource) | 初始化 `EventSource` 类的新实例。 |

### <a name="public-methods"></a>公共方法

| 名称                                 | 描述                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Eventsource:: Add](#add)             | 将追加到当前的事件处理程序集由指定的委托接口表示的事件处理程序`EventSource`对象。                     |
| [Eventsource:: Getsize](#getsize)     | 检索与当前相关联的事件处理程序数`EventSource`对象。                                                                         |
| [Eventsource:: Invokeall](#invokeall) | 调用与当前关联的每个事件处理程序`EventSource`对象使用指定的参数类型和自变量。                                      |
| [Eventsource:: Remove](#remove)       | 删除指定的事件注册标记与当前相关联的事件处理程序集中所表示的事件处理程序`EventSource`对象。 |

### <a name="protected-data-members"></a>受保护的数据成员

| name                                                    | 描述                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [Eventsource:: Addremovelock_](#addremovelock)           | 同步对的访问[targets_](#targets)数组时添加、 删除或调用事件处理程序。                          |
| [Eventsource:: Targets_](#targets)                       | 包含一个或多个事件处理程序的数组。                                                                                           |
| [Eventsource:: Targetspointerlock_](#targetspointerlock) | 同步对内部数据成员的访问，即使在添加、删除或调用此 EventSource 的事件处理程序时也是如此。 |

## <a name="inheritance-hierarchy"></a>继承层次结构

`EventSource`

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL

## <a name="add"></a>Eventsource:: Add

将追加到当前的事件处理程序集由指定的委托接口表示的事件处理程序`EventSource`对象。

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>参数

*delegateInterface*<br/>
为委托对象，表示事件处理程序的接口。

*令牌*<br/>
此操作完成后，表示该事件的句柄。 使用此令牌作为参数[Remove()](#remove)方法，丢弃的事件处理程序。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="addremovelock"></a>Eventsource:: Addremovelock_

同步对的访问[targets_](#targets)数组时添加、 删除或调用事件处理程序。

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>Eventsource:: Eventsource

初始化 `EventSource` 类的新实例。

```cpp
EventSource();
```

## <a name="getsize"></a>Eventsource:: Getsize

检索与当前相关联的事件处理程序数`EventSource`对象。

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>返回值

中的事件处理程序数量[targets_](#targets)。

## <a name="invokeall"></a>Eventsource:: Invokeall

调用与当前关联的每个事件处理程序`EventSource`对象使用指定的参数类型和自变量。

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>参数

*T0*<br/>
第零个事件处理程序自变量的类型。

T1<br/>
第一个事件处理程序自变量的类型。

T2<br/>
第二个事件处理程序自变量的类型。

*T3*<br/>
第三个事件处理程序自变量的类型。

*T4*<br/>
第四个事件处理程序自变量的类型。

*T5*<br/>
第五个事件处理程序自变量的类型。

*T6*<br/>
第六个事件处理程序自变量的类型。

*T7*<br/>
第七个事件处理程序自变量的类型。

*T8*<br/>
第八个事件处理程序自变量的类型。

*T9*<br/>
第九个事件处理程序自变量的类型。

*arg0*<br/>
第零个事件处理程序自变量。

*arg1*<br/>
第一个事件处理程序自变量。

*Arg2*<br/>
第二个事件处理程序自变量。

*arg3*<br/>
第三个事件处理程序自变量。

*了 arg4*<br/>
第四个事件处理程序自变量。

*arg5*<br/>
第五个事件处理程序自变量。

*了 arg6*<br/>
第六个事件处理程序自变量。

*arg7*<br/>
第七事件处理程序自变量。

*arg8*<br/>
第八个事件处理程序自变量。

*arg9*<br/>
第九个事件处理程序自变量。

## <a name="remove"></a>Eventsource:: Remove

删除指定的事件注册标记与当前相关联的事件处理程序集中所表示的事件处理程序`EventSource`对象。

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>参数

*令牌*<br/>
一个表示事件处理程序的句柄。 此令牌已由注册事件处理程序时返回[add （)](#add)方法。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

有关详细信息`EventRegistrationToken`结构，请参阅**Windows::Foundation::EventRegistrationToken 结构**中的主题**Windows 运行时**参考文档。

## <a name="targets"></a>Eventsource:: Targets_

包含一个或多个事件处理程序的数组。

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>备注

当表示由当前事件`EventSource`对象发生，则调用事件处理程序。

## <a name="targetspointerlock"></a>Eventsource:: Targetspointerlock_

此同步对内部数据成员，即使是事件处理程序的访问`EventSource`添加、 删除或被调用。

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
