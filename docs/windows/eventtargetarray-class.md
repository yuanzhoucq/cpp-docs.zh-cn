---
title: "EventTargetArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray
dev_langs: C++
helpviewer_keywords: EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac591a1d27792d3b825336ed46e38fa5d002fa73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="eventtargetarray-class"></a>EventTargetArray 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>备注  
 表示数组的事件处理程序。  
  
 与之关联的事件处理程序[EventSource](../windows/eventsource-class.md)对象存储在受保护的 EventTargetArray 数据成员中。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[EventTargetArray::EventTargetArray 构造函数](../windows/eventtargetarray-eventtargetarray-constructor.md)|初始化 EventTargetArray 类的新实例。|  
|[EventTargetArray::~EventTargetArray 析构函数](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|取消初始化当前 EventTargetArray 类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[EventTargetArray::AddTail 方法](../windows/eventtargetarray-addtail-method.md)|向事件处理程序在内部数组的末尾追加指定的事件处理程序。|  
|[EventTargetArray::Begin 方法](../windows/eventtargetarray-begin-method.md)|获取事件处理程序在内部数组的第一个元素的地址。|  
|[EventTargetArray::End 方法](../windows/eventtargetarray-end-method.md)|获取事件处理程序在内部数组的最后一个元素的地址。|  
|[EventTargetArray::Length 方法](../windows/eventtargetarray-length-method.md)|获取事件处理程序在内部数组元素的当前数目。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `EventTargetArray`  
  
## <a name="requirements"></a>惠?  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)