---
title: "propagator_block 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::propagator_block
dev_langs:
- C++
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: b53577fc187d699f50b4095518e9bc3562dcc7f3
ms.lasthandoff: 02/24/2017

---
# <a name="propagatorblock-class"></a>propagator_block 类
`propagator_block` 类是同时为源和目标的消息块的抽象基类。 它合并了 `source_block` 和 `target_block` 类的功能。  
  
## <a name="syntax"></a>语法  
  
```
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
 public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>参数  
 `_TargetLinkRegistry`  
 若要用来存放目标链接的链接注册表。  
  
 `_SourceLinkRegistry`  
 要用于保存源链接链接注册表。  
  
 `_MessageProcessorType`  
 用于处理邮件的处理器类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|`source_iterator`|有关迭代器的类型`source_link_manager`此`propagator_block`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[propagator_block 构造函数](#ctor)|构造 `propagator_block` 对象。|  
|[~ propagator_block 析构函数](#dtor)|销毁 `propagator_block` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[propagate 方法](#propagate)|消息源块以异步方式传递到此目标块中。|  
|[send 方法](#send)|以同步方式启动到此块的消息。 由调用`ISource`块。 完成此函数后，该消息将已传播到块。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[decline_incoming_messages 方法](#decline_incoming_messages)|指示到块应拒绝新消息。|  
|[initialize_source_and_target 方法](#initialize_source_and_target)|初始化基对象。 具体而言，`message_processor`对象需要将其初始化。|  
|[link_source 方法](#link_source)|指定的源块链接至该`propagator_block`对象。|  
|[process_input_messages 方法](#process_input_messages)|处理输入消息。 这仅可用于从 source_block 派生的传播器块 (重写[source_block:: process_input_messages](source-block-class.md#process_input_messages)。)|  
|[propagate_message 方法](#propagate_message)|当在派生类中重写此方法以异步方式将消息传递从`ISource`至此块`propagator_block`对象。 由调用`propagate`方法时由源块调用。|  
|[register_filter 方法](#register_filter)|注册将调用每个收到的消息的筛选器方法。|  
|[remove_network_links 方法](#remove_network_links)|从这中移除所有源和目标的网络链接`propagator_block`对象。|  
|[send_message 方法](#send_message)|当在派生类中重写此方法以同步方式将消息传递从`ISource`至此块`propagator_block`对象。 由调用`send`方法时由源块调用。|  
|[unlink_source 方法](#unlink_source)|取消链接指定的源块与该`propagator_block`对象。|  
|[unlink_sources 方法](#unlink_sources)|断开所有源块与该都链接`propagator_block`对象。 (重写[itarget:: Unlink_sources](itarget-class.md#unlink_sources)。)|  
  
## <a name="remarks"></a>备注  
 若要避免多个继承，`propagator_block`类继承自`source_block`类和`ITarget`抽象类。 中的功能的大多数`target_block`此处复制类。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 `propagator_block`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namedeclineincomingmessagesa-declineincomingmessages"></a><a name="decline_incoming_messages"></a>decline_incoming_messages 

 指示到块应拒绝新消息。  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>备注  
 若要确保析构时拒绝新消息的析构函数调用此方法。  
  
##  <a name="a-nameinitializesourceandtargeta-initializesourceandtarget"></a><a name="initialize_source_and_target"></a>initialize_source_and_target 

 初始化基对象。 具体而言，`message_processor`对象需要将其初始化。  
  
```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>参数  
 `_PScheduler`  
 要用于计划任务计划程序。  
  
 `_PScheduleGroup`  
 要用于计划任务的计划组。  
  
##  <a name="a-namelinksourcea-linksource"></a><a name="link_source"></a>link_source 

 指定的源块链接至该`propagator_block`对象。  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PSource`  
 一个指向`ISource`相链接的块。  
  
##  <a name="a-nameprocessinputmessagesa-processinputmessages"></a><a name="process_input_messages"></a>process_input_messages 

 处理输入消息。 这只适用于从源块派生的传播器块。  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
  
##  <a name="a-namepropagatea-propagate"></a><a name="propagate"></a>传播 

 消息源块以异步方式传递到此目标块中。  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。  
  
### <a name="remarks"></a>备注  
 `propagate`对目标块链接的源块通过调用方法。 其进行排队以处理该消息，如果一个未排队的异步任务或执行。  
  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果`_PMessage`或`_PSource`参数是`NULL`。  
  
##  <a name="a-namepropagatemessagea-propagatemessage"></a><a name="propagate_message"></a>propagate_message 

 当在派生类中重写此方法以异步方式将消息传递从`ISource`至此块`propagator_block`对象。 由调用`propagate`方法时由源块调用。  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。  
  
##  <a name="a-namectora-propagatorblock"></a><a name="ctor"></a>propagator_block 

 构造 `propagator_block` 对象。  
  
```
propagator_block();
```  
  
##  <a name="a-namedtora-propagatorblock"></a><a name="dtor"></a>~ propagator_block 

 销毁 `propagator_block` 对象。  
  
```
virtual ~propagator_block();
```  
  
##  <a name="a-nameregisterfiltera-registerfilter"></a><a name="register_filter"></a>register_filter 

 注册将调用每个收到的消息的筛选器方法。  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>参数  
 `_Filter`  
 筛选器方法中。  
  
##  <a name="a-nameremovenetworklinksa-removenetworklinks"></a><a name="remove_network_links"></a>remove_network_links 

 从这中移除所有源和目标的网络链接`propagator_block`对象。  
  
```
void remove_network_links();
```  
  
##  <a name="a-namesenda-send"></a><a name="send"></a>发送 

 以同步方式启动到此块的消息。 由调用`ISource`块。 完成此函数后，该消息将已传播到块。  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。  
  
### <a name="remarks"></a>备注  
 此方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果`_PMessage`或`_PSource`参数是`NULL`。  
  
##  <a name="a-namesendmessagea-sendmessage"></a><a name="send_message"></a>send_message 

 当在派生类中重写此方法以同步方式将消息传递从`ISource`至此块`propagator_block`对象。 由调用`send`方法时由源块调用。  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>返回值  
 一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。  
  
### <a name="remarks"></a>备注  
 默认情况下，返回此块`declined`除非由派生类中重写。  
  
##  <a name="a-nameunlinksourcea-unlinksource"></a><a name="unlink_source"></a>unlink_source 

 取消链接指定的源块与该`propagator_block`对象。  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PSource`  
 一个指向`ISource`要取消链接的块。  
  
##  <a name="a-nameunlinksourcesa-unlinksources"></a><a name="unlink_sources"></a>unlink_sources 

 断开所有源块与该都链接`propagator_block`对象。  
  
```
virtual void unlink_sources();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [source_block 类](source-block-class.md)   
 [ITarget 类](itarget-class.md)

