---
title: "call 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
dev_langs: C++
helpviewer_keywords: call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d575aaa01a3668925c6a81eda7d8d99cc591180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="call-class"></a>call 类
`call` 消息块是多源、有序的 `target_block`，可以在接收消息时调用指定函数。  
  
## <a name="syntax"></a>语法  
  
```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 消息的负载类型传播到此块。  
  
 `_FunctorType`  
 此块可以接受的函数的签名。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[调用](#ctor)|已重载。 构造`call`消息块。|  
|[~ call 析构函数](#dtor)|销毁`call`消息块。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[process_input_messages](#process_input_messages)|执行输入消息中调用函数。|  
|[process_message](#process_message)|处理一条消息，已接受此`call`消息块。|  
|[propagate_message](#propagate_message)|以异步方式从将消息传递`ISource`至此块`call`消息块。 由调用`propagate`方法，调用由源块时。|  
|[send_message](#send_message)|以同步方式从将消息传递`ISource`至此块`call`消息块。 由调用`send`方法，调用由源块时。|  
|[supports_anonymous_source](#supports_anonymous_source)|重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。 (重写[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ITarget](itarget-class.md)  
  
 [target_block](target-block-class.md)  
  
 `call`  
  
## <a name="requirements"></a>惠?  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a>调用 

 构造`call`消息块。  
  
```
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>参数  
 `_Func`  
 将为每个接受的消息调用一个函数。  
  
 `_Filter`  
 确定是否应接受提供的消息的筛选器函数。  
  
 `_PScheduler`  
 `Scheduler`对象在其中的传播任务`call`计划消息块。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`对象在其中的传播任务`call`计划消息块。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="remarks"></a>备注  
 如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。  
  
 类型`_Call_method`是具有签名的涵子`void (T const &)`其调用由此`call`处理一条消息的消息块。  
  
 类型`filter_method`是具有签名的涵子`bool (T const &)`其调用由此`call`消息块，以确定它是否应接受提供的消息。  
  
##  <a name="dtor"></a>~ 调用 

 销毁`call`消息块。  
  
```
~call();
```  
  
##  <a name="process_input_messages"></a>process_input_messages 

 执行输入消息中调用函数。  
  
```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
  
##  <a name="process_message"></a>process_message 

 处理一条消息，已接受此`call`消息块。  
  
```
virtual void process_message(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向要处理的消息的指针。  
  
##  <a name="propagate_message"></a>propagate_message 

 以异步方式从将消息传递`ISource`至此块`call`消息块。 由调用`propagate`方法，调用由源块时。  
  
```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
##  <a name="send_message"></a>send_message 

 以同步方式从将消息传递`ISource`至此块`call`消息块。 由调用`send`方法，调用由源块时。  
  
```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>返回值  
 `true` 因为该块没有推迟所提供的消息。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [transformer 类](transformer-class.md)
