---
title: "choice 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::choice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "choice 类"
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# choice 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`choice` 消息块是多源、单目标的块，表示与一组源进行的控制流交互。 choice 块将等待多个源中的任何一个源以生成消息，并将传播生成该消息的源的索引。  
  
## <a name="syntax"></a>语法  
  
```  
template<
    class T  
>  
class choice: public ISource<size_t>;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 一个 `tuple`-基于表示输入源的有效负载类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`type`|类型别名 `T`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[choice:: choice 构造函数](#choice__choice_constructor)|已重载。 构造 `choice` 消息块。|  
|[选择:: ~ choice 析构函数](#choice___dtorchoice_destructor)|销毁 `choice` 消息块。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[choice:: accept 方法](#choice__accept_method)|接受提供的这一条消息 `choice` 块中，将所有权转移给调用方。|  
|[choice:: acquire_ref 方法](#choice__acquire_ref_method)|获取对此的引用计数 `choice` 消息块，以防止删除。|  
|[choice:: consume 方法](#choice__consume_method)|使用以前提供的这一条消息 `choice` 消息块并成功由目标，将所有权转移给调用方保留。|  
|[choice:: has_value 方法](#choice__has_value_method)|检查是否这 `choice` 消息块时尚值初始化。|  
|[choice:: index 方法](#choice__index_method)|返回到一个索引 `tuple` 表示所选的元素 `choice` 消息块。|  
|[choice:: link_target 方法](#choice__link_target_method)|链接至该目标块 `choice` 消息块。|  
|[choice:: release 方法](#choice__release_method)|释放以前的成功消息保留。|  
|[choice:: release_ref 方法](#choice__release_ref_method)|释放此引用计数 `choice` 消息块。|  
|[choice:: reserve 方法](#choice__reserve_method)|保留以前提供的这一条消息 `choice` 消息块。|  
|[choice:: unlink_target 方法](#choice__unlink_target_method)|取消链接从该目标块 `choice` 消息块。|  
|[choice:: unlink_targets 方法](#choice__unlink_targets_method)|取消链接从此所有目标 `choice` 消息块。 (重写 [Isource:: Unlink_targets](../../../parallel/concrt/reference/isource-class.md#isource__unlink_targets_method)。)|  
|[choice:: value 方法](#choice__value_method)|获取其索引已选择的消息 `choice` 消息块。|  
  
## <a name="remarks"></a>备注  
 选择块确保只有一个传入消息使用。  
  
 有关详细信息，请参阅 [异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 `choice`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namechoiceacceptmethoda-choiceaccept-method"></a><a name="choice__accept_method"></a>  choice:: accept 方法  
 接受提供的这一条消息 `choice` 块中，将所有权转移给调用方。  
  
```  
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
  `runtime_object_identity` 的提供 `message` 对象。  
  
 `_PTarget`  
 正在调用的目标块的指针 `accept` 方法。  
  
### <a name="return-value"></a>返回值  
 指向调用方拥有所有权的消息的指针。  
  
##  <a name="a-namechoiceacquirerefmethoda-choiceacquireref-method"></a><a name="choice__acquire_ref_method"></a>  choice:: acquire_ref 方法  
 获取对此的引用计数 `choice` 消息块，以防止删除。  
  
```  
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 此方法由 `ITarget` 对象被链接到此源期间 `link_target` 方法。  
  
##  <a name="a-namechoicechoiceconstructora-choicechoice-constructor"></a><a name="choice__choice_constructor"></a>  choice:: choice 构造函数  
 构造 `choice` 消息块。  
  
```  
explicit choice(
    T _Tuple);

 
choice(
    Scheduler& _PScheduler,  
    T _Tuple);

 
choice(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
choice(
    choice&& _Choice);
```  
  
### <a name="parameters"></a>参数  
 `_Tuple`  
 choice 的源的 `tuple` 。  
  
 `_PScheduler`  
 在其中计划了 `Scheduler` 消息块的传播任务的 `choice` 对象。  
  
 `_PScheduleGroup`  
 在其中计划了 `ScheduleGroup` 消息块的传播任务的 `choice` 对象。 所用 `Scheduler` 对象由该计划组提示。  
  
 `_Choice`  
 要从中进行复制的 `choice` 消息块。 请注意原始对象是孤立的，使之成为一个移动构造函数。  
  
### <a name="remarks"></a>备注  
 如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。  
  
 在锁定状态下不执行移动构造，这意味着应由用户确保在移动期间没有轻量任务处于飞行状态。 否则可能会发生大量争用，从而导致异常或不一致的状态。  
  
##  <a name="a-namechoicedtorchoicedestructora-choicechoice-destructor"></a><a name="choice___dtorchoice_destructor"></a>  选择:: ~ choice 析构函数  
 销毁 `choice` 消息块。  
  
```  
~choice();
```  
  
##  <a name="a-namechoiceconsumemethoda-choiceconsume-method"></a><a name="choice__consume_method"></a>  choice:: consume 方法  
 使用以前提供的这一条消息 `choice` 消息块并成功由目标，将所有权转移给调用方保留。  
  
```  
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
  `runtime_object_identity` 的保留 `message` 对象。  
  
 `_PTarget`  
 正在调用的目标块的指针 `consume` 方法。  
  
### <a name="return-value"></a>返回值  
 一个指向 `message` 对象时调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
  `consume` 方法类似于是 `accept`, ，但始终必须通过调用前面 `reserve` 返回 `true`。  
  
##  <a name="a-namechoicehasvaluemethoda-choicehasvalue-method"></a><a name="choice__has_value_method"></a>  choice:: has_value 方法  
 检查是否这 `choice` 消息块时尚值初始化。  
  
```  
bool has_value() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果块已接收一个值， `false` 否则为。  
  
##  <a name="a-namechoiceindexmethoda-choiceindex-method"></a><a name="choice__index_method"></a>  choice:: index 方法  
 返回到一个索引 `tuple` 表示所选的元素 `choice` 消息块。  
  
```  
size_t index();
```  
  
### <a name="return-value"></a>返回值  
 消息索引。  
  
### <a name="remarks"></a>备注  
 可以使用提取消息负载 `get` 方法。  
  
##  <a name="a-namechoicelinktargetmethoda-choicelinktarget-method"></a><a name="choice__link_target_method"></a>  choice:: link_target 方法  
 链接至该目标块 `choice` 消息块。  
  
```  
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 一个指向 `ITarget` 要链接到此块 `choice` 消息块。  
  
##  <a name="a-namechoicereleasemethoda-choicerelease-method"></a><a name="choice__release_method"></a>  choice:: release 方法  
 释放以前的成功消息保留。  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
  `runtime_object_identity` 的 `message` 对象被释放。  
  
 `_PTarget`  
 正在调用的目标块的指针 `release` 方法。  
  
##  <a name="a-namechoicereleaserefmethoda-choicereleaseref-method"></a><a name="choice__release_ref_method"></a>  choice:: release_ref 方法  
 释放此引用计数 `choice` 消息块。  
  
```  
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 此方法由 `ITarget` 从此源要取消链接的对象。 源块允许释放任何资源为目标块保留。  
  
##  <a name="a-namechoicereservemethoda-choicereserve-method"></a><a name="choice__reserve_method"></a>  choice:: reserve 方法  
 保留以前提供的这一条消息 `choice` 消息块。  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
  `runtime_object_identity` 的 `message` 对象所保留。  
  
 `_PTarget`  
 正在调用的目标块的指针 `reserve` 方法。  
  
### <a name="return-value"></a>返回值  
 `true` 如果消息已成功保留， `false` 否则为。 保留可能因为众多原因失败，包括：消息已保留或已由另一目标接受，源可能拒绝保留等。  
  
### <a name="remarks"></a>备注  
 在您调用之后 `reserve`, ，如果成功，必须调用 `consume` 或 `release` 才能执行或分别放弃的消息的所有权。  
  
##  <a name="a-namechoiceunlinktargetmethoda-choiceunlinktarget-method"></a><a name="choice__unlink_target_method"></a>  choice:: unlink_target 方法  
 取消链接从该目标块 `choice` 消息块。  
  
```  
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 一个指向 `ITarget` 块取消与此链接 `choice` 消息块。  
  
##  <a name="a-namechoiceunlinktargetsmethoda-choiceunlinktargets-method"></a><a name="choice__unlink_targets_method"></a>  choice:: unlink_targets 方法  
 取消链接从此所有目标 `choice` 消息块。  
  
```  
virtual void unlink_targets();
```  
  
### <a name="remarks"></a>备注  
 此方法不需要从析构函数调用，因为析构函数的内部 `single_assignment` 块将正确地取消链接。  
  
##  <a name="a-namechoicevaluemethoda-choicevalue-method"></a><a name="choice__value_method"></a>  choice:: value 方法  
 获取其索引已选择的消息 `choice` 消息块。  
  
```  
template <
    typename _Payload_type  
>  
_Payload_type const& value();
```  
  
### <a name="parameters"></a>参数  
 `_Payload_type`  
 消息负载的类型。  
  
### <a name="return-value"></a>返回值  
 消息的负载。  
  
### <a name="remarks"></a>备注  
 因为 `choice` 消息块可以采用不同负载类型的输入，您必须指定检索时的负载类型。 您可以确定基于的结果类型 `index` 方法。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [join 类](../../../parallel/concrt/reference/join-class.md)   
 [single_assignment 类](../../../parallel/concrt/reference/single-assignment-class.md)
