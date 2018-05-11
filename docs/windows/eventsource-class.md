---
title: EventSource 类 |Microsoft 文档
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b2d466b317927cd8de259637450b68b6aaf13bd5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="eventsource-class"></a>EventSource 类
表示非敏捷事件。 EventSource 成员函数添加、 删除和调用事件处理程序。 对于 agile 事件，使用[AgileEventSource](agileeventsource-class.md)。 
  
## <a name="syntax"></a>语法  
  
```  
template<typename TDelegateInterface>  
class EventSource;  
```  
  
#### <a name="parameters"></a>参数  
 `TDelegateInterface`  
 一个委托，表示一个事件处理程序接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[EventSource::EventSource 构造函数](../windows/eventsource-eventsource-constructor.md)|初始化 EventSource 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[EventSource::Add 方法](../windows/eventsource-add-method.md)|将追加到的事件处理程序当前 EventSource 对象集表示由指定的委托接口的事件处理程序。|  
|[EventSource::GetSize 方法](../windows/eventsource-getsize-method.md)|检索与当前 EventSource 对象关联的事件处理程序数量|  
|[EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)|使用指定自变量类型和自变量调用与当前 EventSource 对象关联的每个事件处理程序。|  
|[EventSource::Remove 方法](../windows/eventsource-remove-method.md)|删除从与当前 EventSource 对象关联的事件处理程序集中指定的事件注册标记所表示的事件处理程序。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[EventSource::addRemoveLock_ 数据成员](../windows/eventsource-addremovelock-data-member.md)|同步访问[targets_](../windows/eventsource-targets-data-member.md)数组时添加、 删除或调用事件处理程序。|  
|[EventSource::targets_ 数据成员](../windows/eventsource-targets-data-member.md)|包含一个或多个事件处理程序的数组。|  
|[EventSource::targetsPointerLock_ 数据成员](../windows/eventsource-targetspointerlock-data-member.md)|同步对内部数据成员的访问，即使在添加、删除或调用此 EventSource 的事件处理程序时也是如此。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `EventSource`  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft:: wrl Namespace](../windows/microsoft-wrl-namespace.md)
[AgileEventSource 类](agileeventsource-class.md)