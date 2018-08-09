---
title: AgileEventSource 类 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- AgileEventSource class
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90a2c582c2740846f90270fe9f45b96871329252
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642833"
---
# <a name="agileeventsource-class"></a>AgileEventSource 类

表示由敏捷组件，可以从任意线程访问一个组件引发的事件。 继承自[EventSource](eventsource-class.md)并重写`Add`成员函数和其他类型参数，用于指定有关如何调用敏捷事件选项。

## <a name="syntax"></a>语法

```cpp
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>参数  
 *TDelegateInterface*  
 一个委托，表示一个事件处理程序接口。

 *TEventSourceOptions*  
 [InvokeModeOptions](invokemodeoptions-structure.md)结构其 invokeMode 字段设置为`InvokeMode::StopOnFirstError`或`InvokeMode::FireAll`。

## <a name="remarks"></a>备注

大多数 Windows 运行时中的组件是敏捷组件。 有关详细信息，请参阅[线程处理和封送处理 (C + + /cli CX)](../cppcx/threading-and-marshaling-c-cx.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

 `EventSource` `AgileEventSource`

## <a name="requirements"></a>要求

 **标头：** event.h

 **命名空间：** Microsoft::WRL

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[AgileEventSource::Add 方法](#add)|将追加到当前的事件处理程序集由指定的委托接口表示的敏捷事件处理程序**AgileEventSource**对象。|

## <a name="add"></a> AgileEventSource::Add 方法

将追加到当前的事件处理程序集由指定的委托接口表示的事件处理程序[EventSource](eventsource-class.md)对象。

### <a name="syntax"></a>语法

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>参数

*delegateInterface*  
为委托对象，表示事件处理程序的接口。

*令牌*  
此操作完成后，表示该事件的句柄。 使用此令牌作为参数`Remove()`方法，丢弃的事件处理程序。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。


## <a name="see-also"></a>请参阅
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)