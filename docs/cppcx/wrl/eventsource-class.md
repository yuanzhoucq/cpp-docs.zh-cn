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
ms.openlocfilehash: bb9151e55d133e3e5d8bf10baeb8448101ad6ce0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371539"
---
# <a name="eventsource-class"></a>EventSource 类

表示非敏捷事件。 `EventSource` 成员函数将添加、删除和调用事件处理程序。 对于敏捷事件，请使用[敏捷事件源](agileeventsource-class.md)。

## <a name="syntax"></a>语法

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>参数

*T委托接口*<br/>
表示事件处理程序的委托的接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

| 名称                                     | 说明                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [事件来源：事件来源](#eventsource) | 初始化 `EventSource` 类的新实例。 |

### <a name="public-methods"></a>公共方法

| 名称                                 | 说明                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [事件来源：添加](#add)             | 将指定委托接口表示的事件处理程序追加到当前`EventSource`对象的事件处理程序集。                     |
| [事件来源：获取 Size](#getsize)     | 检索与当前`EventSource`对象关联的事件处理程序数。                                                                         |
| [事件来源：：全部调用](#invokeall) | 使用指定的参数类型和参数调用与`EventSource`当前对象关联的每个事件处理程序。                                      |
| [事件来源：删除](#remove)       | 从与当前`EventSource`对象关联的事件处理程序集中删除指定事件注册令牌表示的事件处理程序。 |

### <a name="protected-data-members"></a>受保护的数据成员

| 名称                                                    | 说明                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [活动来源：addRemoveLock_](#addremovelock)           | 在添加、删除或调用事件处理程序时同步对[targets_](#targets)数组的访问。                          |
| [活动来源：：targets_](#targets)                       | 包含一个或多个事件处理程序的数组。                                                                                           |
| [活动来源：targetsPointerLock_](#targetspointerlock) | 同步对内部数据成员的访问，即使在添加、删除或调用此 EventSource 的事件处理程序时也是如此。 |

## <a name="inheritance-hierarchy"></a>继承层次结构

`EventSource`

## <a name="requirements"></a>要求

**标题：** 事件.h

**命名空间：** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a>事件来源：添加

将指定委托接口表示的事件处理程序追加到当前`EventSource`对象的事件处理程序集。

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>参数

*委托接口*<br/>
委托对象的接口，该对象表示事件处理程序。

*令 牌*<br/>
此操作完成后，表示事件的句柄。 使用此令牌作为[Remove（）](#remove)方法的参数来丢弃事件处理程序。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a>活动来源：addRemoveLock_

在添加、删除或调用事件处理程序时同步对[targets_](#targets)数组的访问。

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a>事件来源：事件来源

初始化 `EventSource` 类的新实例。

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a>事件来源：获取 Size

检索与当前`EventSource`对象关联的事件处理程序数。

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>返回值

[targets_](#targets)中的事件处理程序数。

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a>事件来源：：全部调用

使用指定的参数类型和参数调用与`EventSource`当前对象关联的每个事件处理程序。

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

*T1*<br/>
第一个事件处理程序自变量的类型。

*T2*<br/>
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
第八个事件处理程序参数的类型。

*T9*<br/>
第九个事件处理程序自变量的类型。

*arg0*<br/>
第零个事件处理程序自变量。

*arg1*<br/>
第一个事件处理程序参数。

*arg2*<br/>
第二个事件处理程序自变量。

*arg3*<br/>
第三个事件处理程序自变量。

*arg4*<br/>
第四个事件处理程序参数。

*arg5*<br/>
第五个事件处理程序自变量。

*arg6*<br/>
第六个事件处理程序参数。

*arg7*<br/>
第七事件处理程序自变量。

*arg8*<br/>
第八个事件处理程序参数。

*arg9*<br/>
第九个事件处理程序参数。

## <a name="eventsourceremove"></a><a name="remove"></a>事件来源：删除

从与当前`EventSource`对象关联的事件处理程序集中删除指定事件注册令牌表示的事件处理程序。

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>参数

*令 牌*<br/>
表示事件处理程序的句柄。 当[Add（）](#add)方法注册事件处理程序时，将返回此令牌。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

有关`EventRegistrationToken`结构的详细信息，请参阅**Windows 运行时**参考文档中的**Windows：基础：：事件注册令牌结构**主题。

## <a name="eventsourcetargets_"></a><a name="targets"></a>活动来源：：targets_

包含一个或多个事件处理程序的数组。

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>备注

当由当前`EventSource`对象表示的事件发生时，将调用事件处理程序。

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a>活动来源：targetsPointerLock_

同步对内部数据成员的访问，即使正在添加、删除或调用`EventSource`此事件处理程序也是如此。

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
