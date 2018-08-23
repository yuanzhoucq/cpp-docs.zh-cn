---
title: DeferrableEventArgs 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a53e33d55ccfac7eff763e53240295ea9b7b2a1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600966"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs 类

一种用于延迟的事件自变量类型的模板类。

## <a name="syntax"></a>语法

```cpp
template <
typename TEventArgsInterface,
typename TEventArgsClass
>
class DeferrableEventArgs : public TEventArgsInterface
```

### <a name="parameters"></a>参数

*TEventArgsInterface*  
声明延迟事件的自变量的接口类型。

*TEventArgsClass*  
实现的类*TEventArgsInterface*。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[DeferrableEventArgs::GetDeferral 方法](../windows/deferrableeventargs-getdeferral-method.md)|获取对[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)表示延迟的事件的对象。|
|[DeferrableEventArgs::InvokeAllFinished 方法](../windows/deferrableeventargs-invokeallfinished-method.md)|调用以指示处理延迟事件的全部过程都已完成。|

## <a name="remarks"></a>备注

将此类的实例传递给延迟事件的事件句柄。 模板参数表示一个接口，该接口为特定类型的延迟事件定义事件参数的详细信息以及定义实现该接口的类。

此类显示为一个延迟事件的事件处理程序的第一个自变量。 您可以调用[GetDeferral](../windows/deferrableeventargs-getdeferral-method.md)方法来获取[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)可以从中获取有关延迟事件的所有信息的对象。 处理完事件后，应对 Deferral 对象调用 Complete。 然后应调用[InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md)在事件处理程序方法结束时，可确保所有延迟事件的完成已正确传递。

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)