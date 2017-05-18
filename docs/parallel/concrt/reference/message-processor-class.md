---
title: "message_processor 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: dff934584179cc58d884be65fdb96cb6c646a4ac
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="messageprocessor-class"></a>message_processor 类
`message_processor` 类是用于处理 `message` 对象的抽象基类。 不能保证消息的排序。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class message_processor;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 在消息中的负载的数据类型由`message_processor`对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`type`|类型别名`T`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[async_send](#async_send)|当在派生类中重写，以异步方式将消息放置到块中。|  
|[sync_send](#sync_send)|当在派生类中重写，以同步方式将消息放置到块中。|  
|[等待](#wait)|当在派生类中重写，等待所有异步操作完成。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|当在派生类中重写，执行到块转发的消息处理。 每次添加一个新消息并找到队列为空，则调用一次。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `message_processor`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="async_send"></a>async_send 

 当在派生类中重写，以异步方式将消息放置到块中。  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Msg`  
 一个`message`对象异步发送。  
  
### <a name="remarks"></a>备注  
 处理器实现应重写此方法。  
  
##  <a name="process_incoming_message"></a>process_incoming_message 

 当在派生类中重写，执行到块转发的消息处理。 每次添加一个新消息并找到队列为空，则调用一次。  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>备注  
 消息块实现应重写此方法。  
  
##  <a name="sync_send"></a>sync_send 

 当在派生类中重写，以同步方式将消息放置到块中。  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Msg`  
 一个`message`对象来同步发送。  
  
### <a name="remarks"></a>备注  
 处理器实现应重写此方法。  
  
##  <a name="wait"></a>等待 

 当在派生类中重写，等待所有异步操作完成。  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>备注  
 处理器实现应重写此方法。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ordered_message_processor 类](ordered-message-processor-class.md)

