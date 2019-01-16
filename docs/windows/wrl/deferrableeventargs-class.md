---
title: DeferrableEventArgs 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
ms.openlocfilehash: 509686556bd06a6ec9d059593be46d0fc6a3876d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335753"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs 类

一种用于延迟的事件自变量类型的模板类。

## <a name="syntax"></a>语法

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>参数

*TEventArgsInterface*<br/>
声明延迟事件的自变量的接口类型。

*TEventArgsClass*<br/>
实现的类*TEventArgsInterface*。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

名称                                                         | 描述
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[DeferrableEventArgs::GetDeferral](#getdeferral)             | 获取对[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)表示延迟的事件的对象。
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | 调用以指示处理延迟事件的全部过程都已完成。

## <a name="remarks"></a>备注

将此类的实例传递给延迟事件的事件句柄。 模板参数表示一个接口，该接口为特定类型的延迟事件定义事件参数的详细信息以及定义实现该接口的类。

此类显示为一个延迟事件的事件处理程序的第一个自变量。 您可以调用[GetDeferral](#getdeferral)方法来获取[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)可以从中获取有关延迟事件的所有信息的对象。 处理完事件后，应对 Deferral 对象调用 Complete。 然后应调用[InvokeAllFinished](#invokeallfinished)在事件处理程序方法结束时，可确保所有延迟事件的完成已正确传递。

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft:: wrl

## <a name="getdeferral"></a>DeferrableEventArgs::GetDeferral

获取对[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)表示延迟的事件的对象。

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>参数

*result*<br/>
将引用的指针[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)对象在调用完成时。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="invokeallfinished"></a>DeferrableEventArgs::InvokeAllFinished

调用以指示处理延迟事件的全部过程都已完成。

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>备注

应在事件源调用后调用此方法[InvokeAll](eventsource-class.md#invokeall)。 调用此方法将阻止发生进一步的延迟，并且如果没有发生延迟将强制完成处理程序来执行。
