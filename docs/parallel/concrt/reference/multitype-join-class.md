---
title: "multitype_join 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::multitype_join
dev_langs:
- C++
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
caps.latest.revision: 20
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
ms.openlocfilehash: 71f644331cbaef8322176e554c52a14d59f6d75a
ms.lasthandoff: 02/24/2017

---
# <a name="multitypejoin-class"></a>multitype_join 类
`multitype_join` 消息块是多源、单目标的消息块，可以合并来自其每个源的不同类型的消息并向其目标提供合并的消息的元组。  
  
## <a name="syntax"></a>语法  
  
```  
template<
    typename T,  
    join_type _Jtype = non_greedy  
>  
class multitype_join: public ISource<typename _Unwrap<T>::type>;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 `tuple`加入和传播由块的消息的负载类型。  
  
 `_Jtype`  
 类型的`join`块，此元素，也`greedy`或`non_greedy`  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`type`|类型别名`T`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[multitype_join 构造函数](#ctor)|已重载。 构造 `multitype_join` 消息块。|  
|[~ multitype_join 析构函数](#dtor)|销毁`multitype_join`消息块。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[accept 方法](#accept)|接受提供的这一条消息`multitype_join`块中，将所有权转移给调用方。|  
|[acquire_ref 方法](#acquire_ref)|获取对此的引用计数`multitype_join`消息块，以防止删除。|  
|[consume 方法](#consume)|使用以前提供的消息`multitype_join`消息块并成功由目标，将所有权转移给调用方保留。|  
|[link_target 方法](#link_target)|链接至该目标块`multitype_join`消息块。|  
|[release 方法](#release)|释放以前的成功消息保留。|  
|[release_ref 方法](#release_ref)|释放此引用计数`multiple_join`消息块。|  
|[reserve 方法](#reserve)|保留以前提供的这一条消息`multitype_join`消息块。|  
|[unlink_target 方法](#unlink_target)|断开与该目标块的链接`multitype_join`消息块。|  
|[unlink_targets 方法](#unlink_targets)|取消链接从此所有目标`multitype_join`消息块。 (重写[isource:: Unlink_targets](isource-class.md#unlink_targets)。)|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ISource](isource-class.md)  
  
 `multitype_join`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameaccepta-accept"></a><a name="accept"></a>接受 

 接受提供的这一条消息`multitype_join`块中，将所有权转移给调用方。  
  
```  
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`accept`方法。  
  
### <a name="return-value"></a>返回值  
 指向调用方拥有所有权的消息的指针。  
  
##  <a name="a-nameacquirerefa-acquireref"></a><a name="acquire_ref"></a>acquire_ref 

 获取对此的引用计数`multitype_join`消息块，以防止删除。  
  
```  
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 此方法由`ITarget`对象被链接到此源期间`link_target`方法。  
  
##  <a name="a-nameconsumea-consume"></a><a name="consume"></a>使用 

 使用以前提供的消息`multitype_join`消息块并成功由目标，将所有权转移给调用方保留。  
  
```  
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的保留`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`consume`方法。  
  
### <a name="return-value"></a>返回值  
 一个指向`message`对象时调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 `consume`方法类似于是`accept`，但始终必须通过调用前面`reserve`返回`true`。  
  
##  <a name="a-namelinktargeta-linktarget"></a><a name="link_target"></a>link_target 

 链接至该目标块`multitype_join`消息块。  
  
```  
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 一个指向`ITarget`块要链接到此`multitype_join`消息块。  
  
##  <a name="a-namectora-multitypejoin"></a><a name="ctor"></a>multitype_join 

 构造 `multitype_join` 消息块。  
  
```  
explicit multitype_join(
    T _Tuple);

 
multitype_join(
    Scheduler& _PScheduler,  
    T _Tuple);

 
multitype_join(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
multitype_join(
    multitype_join&& _Join);
```  
  
### <a name="parameters"></a>参数  
 `_Tuple`  
 此 `tuple` 消息块的源的 `multitype_join` 。  
  
 `_PScheduler`  
 在其中计划了 `Scheduler` 消息块的传播任务的 `multitype_join` 对象。  
  
 `_PScheduleGroup`  
 在其中计划了 `ScheduleGroup` 消息块的传播任务的 `multitype_join` 对象。 所用 `Scheduler` 对象由该计划组提示。  
  
 `_Join`  
 要从中进行复制的 `multitype_join` 消息块。 请注意原始对象是孤立的，使之成为一个移动构造函数。  
  
### <a name="remarks"></a>备注  
 如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。  
  
 在锁定状态下不执行移动构造，这意味着应由用户确保在移动期间没有轻量任务处于飞行状态。 否则可能会发生大量争用，从而导致异常或不一致的状态。  
  
##  <a name="a-namedtora-multitypejoin"></a><a name="dtor"></a>~ multitype_join 

 销毁`multitype_join`消息块。  
  
```  
~multitype_join();
```  
  
##  <a name="a-namereleasea-release"></a><a name="release"></a>版本 

 释放以前的成功消息保留。  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象被释放。  
  
 `_PTarget`  
 正在调用的目标块的指针`release`方法。  
  
##  <a name="a-namereleaserefa-releaseref"></a><a name="release_ref"></a>release_ref 

 释放此引用计数`multiple_join`消息块。  
  
```  
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 此方法由`ITarget`从此源要取消链接的对象。 源块允许释放任何资源为目标块保留。  
  
##  <a name="a-namereservea-reserve"></a><a name="reserve"></a>保留 

 保留以前提供的这一条消息`multitype_join`消息块。  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象所保留。  
  
 `_PTarget`  
 正在调用的目标块的指针`reserve`方法。  
  
### <a name="return-value"></a>返回值  
 `true`如果消息已成功保留，`false`否则为。 保留可能因为众多原因失败，包括：消息已保留或已由另一目标接受，源可能拒绝保留等。  
  
### <a name="remarks"></a>备注  
 在您调用之后`reserve`，如果成功，必须调用`consume`或`release`才能执行或分别放弃的消息的所有权。  
  
##  <a name="a-nameunlinktargeta-unlinktarget"></a><a name="unlink_target"></a>unlink_target 

 断开与该目标块的链接`multitype_join`消息块。  
  
```  
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 一个指向`ITarget`块取消与此链接`multitype_join`消息块。  
  
##  <a name="a-nameunlinktargetsa-unlinktargets"></a><a name="unlink_targets"></a>unlink_targets 

 取消链接从此所有目标`multitype_join`消息块。  
  
```  
virtual void unlink_targets();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [choice 类](choice-class.md)   
 [join 类](join-class.md)

