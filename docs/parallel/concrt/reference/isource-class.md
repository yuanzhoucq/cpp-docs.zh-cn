---
title: "ISource 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 147623329d71da704529c12e27ce3c768c1b8145
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="isource-class"></a>ISource 类
`ISource` 类是所有源块的接口。 源块将消息传播到 `ITarget` 块。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class ISource;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 源块所生成的消息中的负载的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`source_type`|类型别名`T`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[~ ISource 析构函数](#dtor)|销毁`ISource`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[accept](#accept)|当在派生类中重写，接受一条消息，已提供此`ISource`块，将所有权转让给调用方。|  
|[acquire_ref](#acquire_ref)|当在派生类中重写，获取对此引用计数`ISource`块，以防止删除。|  
|[consume](#consume)|在派生类中重写，会使用以前提供的这一条消息`ISource`阻止并成功由目标，将所有权转让给调用方保留。|  
|[link_target](#link_target)|当在派生类中重写，链接至该目标块`ISource`块。|  
|[release](#release)|当在派生类中重写，释放以前的成功的消息保留。|  
|[release_ref](#release_ref)|当在派生类中重写时释放引用计数这`ISource`块。|  
|[reserve](#reserve)|当在派生类中重写时保留以前提供的这一条消息`ISource`块。|  
|[unlink_target](#unlink_target)|当在派生类中重写，传递取消链接目标块与该`ISource`块，如果发现已链接。|  
|[unlink_targets](#unlink_targets)|当在派生类中重写，传递取消链接所有目标块与该`ISource`块。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISource`  
  
## <a name="requirements"></a>惠?  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="accept"></a> 接受 

 当在派生类中重写，接受一条消息，已提供此`ISource`块，将所有权转让给调用方。  
  
```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`accept`方法。  
  
### <a name="return-value"></a>返回值  
 指向调用方现在具有的所有权的消息的指针。  
  
### <a name="remarks"></a>备注  
 `accept`正在由此提供一条消息时，调用方法目标`ISource`块。 消息指针返回可能不同于传递给`propagate`方法`ITarget`块，如果此源决定消息的副本。  
  
##  <a name="acquire_ref"></a> acquire_ref 

 当在派生类中重写，获取对此引用计数`ISource`块，以防止删除。  
  
```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法`ITarget`正在链接到在此源的对象`link_target`方法。  
  
##  <a name="consume"></a> 使用 

 在派生类中重写，会使用以前提供的这一条消息`ISource`阻止并成功由目标，将所有权转让给调用方保留。  
  
```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的保留`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`consume`方法。  
  
### <a name="return-value"></a>返回值  
 指向的指针`message`对象调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 `consume`方法类似于是`accept`，但始终之前必须通过调用`reserve`返回`true`。  
  
##  <a name="dtor"></a> ~ISource 

 销毁`ISource`对象。  
  
```
virtual ~ISource();
```  
  
##  <a name="link_target"></a> link_target 

 当在派生类中重写，链接至该目标块`ISource`块。  
  
```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 链接到此目标块的指针`ISource`块。  
  
##  <a name="release"></a> 版本 

 当在派生类中重写，释放以前的成功的消息保留。  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的保留`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`release`方法。  
  
##  <a name="release_ref"></a> release_ref 

 当在派生类中重写时释放引用计数这`ISource`块。  
  
```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法`ITarget`正在取消链接从该源的对象。 源块可以释放为目标块保留任何资源。  
  
##  <a name="reserve"></a> 保留 

 当在派生类中重写时保留以前提供的这一条消息`ISource`块。  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`reserve`方法。  
  
### <a name="return-value"></a>返回值  
 `true` 如果消息已成功保留，`false`否则为。 保留可能因为众多原因失败，包括：消息已保留或已由另一目标接受，源可能拒绝保留等。  
  
### <a name="remarks"></a>备注  
 调用后`reserve`，如果成功，必须调用`consume`或`release`才能采取或分别放弃的消息，拥有。  
  
##  <a name="unlink_target"></a> unlink_target 

 当在派生类中重写，传递取消链接目标块与该`ISource`块，如果发现已链接。  
  
```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向要取消链接至此的目标块`ISource`块。  
  
##  <a name="unlink_targets"></a> unlink_targets 

 当在派生类中重写，传递取消链接所有目标块与该`ISource`块。  
  
```
virtual void unlink_targets() = 0;
```  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ITarget 类](itarget-class.md)
