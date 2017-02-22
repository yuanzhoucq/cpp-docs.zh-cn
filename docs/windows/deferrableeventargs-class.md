---
title: "DeferrableEventArgs 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# DeferrableEventArgs 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种用于延迟的事件参数类型的模板类。  
  
## 语法  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
  
```  
  
#### 参数  
 `TEventArgsInterface`  
 声明延迟事件的参数的接口类型。  
  
 `TEventArgsClass`  
 可实现 `TEventArgsInterface` 的类。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[DeferrableEventArgs::GetDeferral 方法](../windows/deferrableeventargs-getdeferral-method.md)|获取对[延迟](http://go.microsoft.com/fwlink/?LinkId=526520)对象的引用，该对象表示延迟的事件。|  
|[DeferrableEventArgs::InvokeAllFinished 方法](../windows/deferrableeventargs-invokeallfinished-method.md)|调用以指示处理延迟事件的全部过程都已完成。|  
  
## 备注  
 将此类的实例传递给延迟事件的事件句柄。  模板参数表示一个接口，该接口为特定类型的延迟事件定义事件参数的详细信息以及定义实现该接口的类。  
  
 此类显示为一个延迟事件的事件处理程序的第一个参数。  可调用 [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) 方法来获取一个 [Deferral](http://go.microsoft.com/fwlink/?LinkId=526520) 对象，从该对象可获取有关延迟事件的所有信息。  处理完事件后，应对 Deferral 对象调用 Complete。  然后应在事件处理程序方法末尾调用 [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md)，可确保所有延迟事件的完成已正确传递。  
  
## 要求  
 **标头：**event.h  
  
 **命名空间：**Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)