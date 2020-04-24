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
ms.openlocfilehash: 066918bf2c76b17f06871ee08be674be9b36c161
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032455"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs 类

一种用于延迟事件的事件参数类型的模板类。

## <a name="syntax"></a>语法

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>参数

*TEventArgs接口*<br/>
声明延迟事件的自变量的接口类型。

*TEventArgs 类*<br/>
实现*TEventArgs 接口*的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

| 名称 | 说明 |
|--|--|
| [可推断事件：：获取递延](#getdeferral) | 获取对表示延迟事件的[延迟](/uwp/api/windows.foundation.deferral)对象的引用。 |
| [可推断事件阿格：：调用全部完成](#invokeallfinished) | 调用以指示处理延迟事件的全部过程都已完成。 |

## <a name="remarks"></a>备注

将此类的实例传递给延迟事件的事件句柄。 模板参数表示一个接口，该接口为特定类型的延迟事件定义事件自变量的详细信息以及定义实现该接口的类。

此类显示为一个延迟事件的事件处理程序的第一个参数。 您可以调用[GetDeferral](#getdeferral)方法来获取[Deferral](/uwp/api/windows.foundation.deferral)对象，从中您可以获取有关延迟事件的所有信息。 处理完事件后，应对 Deferral 对象调用 Complete。 然后，应在事件处理程序方法的末尾调用[InvokeAllEnd，](#invokeallfinished)以确保正确传达所有延迟事件的完成。

## <a name="requirements"></a>要求

**标题：** 事件.h

**命名空间：** Microsoft::WRL

## <a name="deferrableeventargsgetdeferral"></a><a name="getdeferral"></a>可推断事件：：获取递延

获取对表示延迟事件的[延迟](/uwp/api/windows.foundation.deferral)对象的引用。

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>参数

*结果*<br/>
调用完成后引用[延迟](/uwp/api/windows.foundation.deferral)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="deferrableeventargsinvokeallfinished"></a><a name="invokeallfinished"></a>可推断事件阿格：：调用全部完成

调用以指示处理延迟事件的全部过程都已完成。

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>备注

应在事件源调用[InvokeAll](eventsource-class.md#invokeall)后调用此方法。 调用此方法将阻止发生进一步的延迟，并且如果没有发生延迟将强制完成处理程序来执行。
