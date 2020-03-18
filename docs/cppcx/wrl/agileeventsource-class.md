---
title: AgileEventSource 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: 7a919c0b2aa778ba1db19c3bfc3871542e8f9569
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441265"
---
# <a name="agileeventsource-class"></a>AgileEventSource 类

表示由 agile 组件引发的事件，该组件是可从任何线程访问的组件。 继承自[EventSource](eventsource-class.md) ，并使用附加类型参数重写 `Add` 成员函数，以便为如何调用 agile 事件指定选项。

## <a name="syntax"></a>语法

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>参数

*TDelegateInterface*<br/>
表示事件处理程序的委托的接口。

*TEventSourceOptions*<br/>
[InvokeModeOptions](invokemodeoptions-structure.md)结构，其 invokeMode 字段设置为 `InvokeMode::StopOnFirstError` 或 `InvokeMode::FireAll`。

## <a name="remarks"></a>备注

Windows 运行时中的绝大部分组件都是 agile 组件。 有关详细信息，请参阅[线程处理和C++封送处理（/cx）](../../cppcx/threading-and-marshaling-c-cx.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>要求

**标头：** 事件。h

**命名空间：** Microsoft::WRL

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[AgileEventSource：： Add 方法](#add)|将指定委托接口表示的敏捷事件处理程序追加到当前**AgileEventSource**对象的事件处理程序集。|

## <a name="add"></a>AgileEventSource：： Add 方法

将指定委托接口表示的事件处理程序追加到当前[EventSource](eventsource-class.md)对象的事件处理程序集。

### <a name="syntax"></a>语法

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>参数

*delegateInterface*<br/>
委托对象的接口，它表示事件处理程序。

*token*<br/>
此操作完成后，表示事件的句柄。 使用此标记作为 `Remove()` 方法的参数以放弃事件处理程序。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)