---
title: AgileEventSource 类 |Microsoft 文档
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
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
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d025fc2be86fb5b59107d1deee39962c3c6db04
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="agileeventsource-class"></a>AgileEventSource 类
表示一个敏捷事件。 继承自[EventSource](eventsource-class.md)和替代`Add`用于指定如何调用敏捷事件选项的其他类型参数的成员函数。
  
## <a name="syntax"></a>语法  
  
```  
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```  
  
#### <a name="parameters"></a>参数  
 `TDelegateInterface`  
 一个委托，表示一个事件处理程序接口。

 `TEventSourceOptions` [InvokeModeOptions](invokemodeoptions-structure.md)结构其 invokeMode 字段设置为`InvokeMode::StopOnFirstError`或`InvokeMode::FireAll`。

## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[AgileEventSource::Add 方法](#add)|将追加到的事件处理程序的当前 AgileEventSource 对象集表示由指定的委托接口敏捷事件处理程序。|  

## <a name="add"></a> AgileEventSource::Add 方法

将追加到的事件处理程序当前 EventSource 对象集表示由指定的委托接口的事件处理程序。

### <a name="syntax"></a>语法

```cpp
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);
```

### <a name="parameters"></a>参数

*delegateInterface*

与委托的对象，它表示一个事件处理程序接口。

*令牌*此操作完成后，一个表示事件句柄。 使用此令牌作为 remove （） 方法的参数以放弃事件处理程序。

### <a name="return-value"></a>返回值
如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="inheritance-hierarchy"></a>继承层次结构  
 `EventSource`  
 `AgileEventSource`
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)