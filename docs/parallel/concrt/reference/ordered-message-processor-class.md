---
title: "ordered_message_processor 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83f3181d797b0146cc7e57950da6b5e9569b2ab1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor 类
`ordered_message_processor` 是允许消息块按接收顺序处理消息的 `message_processor`。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class ordered_message_processor : public message_processor<T>;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 由处理器进行处理的消息的负载类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`type`|类型别名`T`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[ordered_message_processor](#ctor)|构造 `ordered_message_processor` 对象。|  
|[~ordered_message_processor Destructor](#dtor)|销毁`ordered_message_processor`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[async_send](#async_send)|异步消息进行排队，并开始处理任务，如果这不完成了已。 (重写[message_processor:: async_send](message-processor-class.md#async_send)。)|  
|[initialize](#initialize)|初始化`ordered_message_processor`与相应的回调函数、 计划程序和计划组的对象。|  
|[initialize_batched_processing](#initialize_batched_processing)|初始化消息的批处理|  
|[sync_send](#sync_send)|同步消息进行排队，并启动处理任务，如果这不完成了已。 (重写[message_processor:: sync_send](message-processor-class.md#sync_send)。)|  
|[wait](#wait)|消息块的析构函数中的使用以确保所有异步处理任务有时间完成，然后销毁块特定于处理器的自旋等待。 (重写[message_processor:: wait](message-processor-class.md#wait)。)|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|以异步方式调用的处理函数。 它将消息取消排队，并开始处理它们。 (重写[message_processor:: process_incoming_message](message-processor-class.md#process_incoming_message)。)|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [message_processor](message-processor-class.md)  
  
 `ordered_message_processor`  
  
## <a name="requirements"></a>惠?  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="async_send"></a> async_send 

 异步消息进行排队，并开始处理任务，如果这不完成了已。  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>参数  
 `_Msg`  
 一条消息指向的指针。  
  
##  <a name="initialize"></a> 初始化 

 初始化`ordered_message_processor`与相应的回调函数、 计划程序和计划组的对象。  
  
```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```  
  
### <a name="parameters"></a>参数  
 `_PScheduler`  
 指向要用于计划轻量任务的计划程序的指针。  
  
 `_PScheduleGroup`  
 指向要用于计划轻量任务的计划组的指针。  
  
 `_Handler`  
 在回调过程中调用处理程序函数。  
  
##  <a name="initialize_batched_processing"></a> initialize_batched_processing 

 初始化消息的批处理  
  
```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```  
  
### <a name="parameters"></a>参数  
 `_Processor`  
 在回调过程中调用处理器函子。  
  
 `_Propagator`  
 在回调过程中调用传播器函子。  
  
##  <a name="ctor"></a> ordered_message_processor 

 构造 `ordered_message_processor` 对象。  
  
```
ordered_message_processor();
```  
  
### <a name="remarks"></a>备注  
 这`ordered_message_processor`将计划异步或同步的处理程序，直到`initialize`调用函数。  
  
##  <a name="dtor"></a> ~ordered_message_processor 

 销毁`ordered_message_processor`对象。  
  
```
virtual ~ordered_message_processor();
```  
  
### <a name="remarks"></a>备注  
 销毁处理器之前等待所有未完成的异步操作。  
  
##  <a name="process_incoming_message"></a> process_incoming_message 

 以异步方式调用的处理函数。 它将消息取消排队，并开始处理它们。  
  
```
virtual void process_incoming_message();
```  
  
##  <a name="sync_send"></a> sync_send 

 同步消息进行排队，并启动处理任务，如果这不完成了已。  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>参数  
 `_Msg`  
 一条消息指向的指针。  
  
##  <a name="wait"></a> 等待 

 消息块的析构函数中的使用以确保所有异步处理任务有时间完成，然后销毁块特定于处理器的自旋等待。  
  
```
virtual void wait();
```  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
