---
title: "EventSource 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EventSource 类"
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# EventSource 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一个事件。  事件源成员函数添加，移除，然后调用事件处理程序。  
  
## 语法  
  
```  
template<  
   typename TDelegateInterface  
>  
class EventSource;  
```  
  
#### 参数  
 `TDelegateInterface`  
 为表示事件处理程序委托的接口。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[EventSource::EventSource 构造函数](../windows/eventsource-eventsource-constructor.md)|初始化 EventSource 类的新实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[EventSource::Add 方法](../windows/eventsource-add-method.md)|附加指定的委托表示接口的事件处理程序设置为当前 EventSource 组对象的事件处理程序。|  
|[EventSource::GetSize 方法](../windows/eventsource-getsize-method.md)|事件处理程序检索的次数与当前 EventSource 对象|  
|[EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)|调用每一个事件处理程序与当前对象 EventSource 使用指定的参数类型和参数。|  
|[EventSource::Remove 方法](../windows/eventsource-remove-method.md)|删除一组指定的事件注册标记表示的事件处理程序关联的事件处理程序 EventSource 当前对象。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[EventSource::addRemoveLock\_ 数据成员](../windows/eventsource-addremovelock-data-member.md)|当添加，移除或调用事件处理程序时，同步向 [targets\_](../windows/eventsource-targets-data-member.md) 数组的访问。|  
|[EventSource::targets\_ 数据成员](../windows/eventsource-targets-data-member.md)|一组一个或多个事件处理程序。|  
|[EventSource::targetsPointerLock\_ 数据成员](../windows/eventsource-targetspointerlock-data-member.md)|甚至，在此 EventSource 的事件处理程序被添加，移除或调用时，同步对内部数据成员的访问权限。|  
  
## 继承层次结构  
 `EventSource`  
  
## 要求  
 **标头：**event.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)