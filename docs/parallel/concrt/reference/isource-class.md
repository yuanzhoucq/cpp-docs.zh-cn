---
title: "ISource 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::ISource
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
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
ms.openlocfilehash: db3ba296a96b2e77c0ae7d9be3d0a499fe2e7f76
ms.lasthandoff: 02/24/2017

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
 源块生成的消息内负载的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|`source_type`|类型别名`T`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[~ ISource 析构函数](#dtor)|销毁`ISource`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[accept 方法](#accept)|当在派生类中重写，接受提供的这一条消息`ISource`块中，将所有权转移给调用方。|  
|[acquire_ref 方法](#acquire_ref)|当在派生类中重写，将获取对此的引用计数`ISource`块中，以防止删除。|  
|[consume 方法](#consume)|在派生类中重写，会使用以前提供的这一条消息`ISource`阻止并成功由目标，将所有权转移给调用方保留。|  
|[link_target 方法](#link_target)|当在派生类中重写链接至该目标块`ISource`块。|  
|[release 方法](#release)|当在派生类中重写，释放以前成功的消息保留。|  
|[release_ref 方法](#release_ref)|当在派生类中重写，将释放对此的引用计数`ISource`块。|  
|[reserve 方法](#reserve)|当在派生类中重写时保留以前提供的这一条消息`ISource`块。|  
|[unlink_target 方法](#unlink_target)|当在派生类中重写，将取消目标块与该链接`ISource`块，如果发现已链接。|  
|[unlink_targets 方法](#unlink_targets)|当在派生类中重写，将取消所有目标块与该都链接`ISource`块。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISource`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameaccepta-accept"></a><a name="accept"></a>接受 

 当在派生类中重写，接受提供的这一条消息`ISource`块中，将所有权转移给调用方。  
  
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
 指向调用方拥有所有权的消息的指针。  
  
### <a name="remarks"></a>备注  
 `accept`正在由此提供一条消息时，调用目标方法`ISource`块。 消息指针返回可能不同于传递到`propagate`方法`ITarget`块，如果此源决定以使该消息的副本。  
  
##  <a name="a-nameacquirerefa-acquireref"></a><a name="acquire_ref"></a>acquire_ref 

 当在派生类中重写，将获取对此的引用计数`ISource`块中，以防止删除。  
  
```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 此方法由`ITarget`对象被链接到此源期间`link_target`方法。  
  
##  <a name="a-nameconsumea-consume"></a><a name="consume"></a>使用 

 在派生类中重写，会使用以前提供的这一条消息`ISource`阻止并成功由目标，将所有权转移给调用方保留。  
  
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
 一个指向`message`对象时调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 `consume`方法类似于是`accept`，但始终必须通过调用前面`reserve`返回`true`。  
  
##  <a name="a-namedtora-isource"></a><a name="dtor"></a>~ ISource 

 销毁`ISource`对象。  
  
```
virtual ~ISource();
```  
  
##  <a name="a-namelinktargeta-linktarget"></a><a name="link_target"></a>link_target 

 当在派生类中重写链接至该目标块`ISource`块。  
  
```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 链接到此目标块的指针`ISource`块。  
  
##  <a name="a-namereleasea-release"></a><a name="release"></a>版本 

 当在派生类中重写，释放以前成功的消息保留。  
  
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
  
##  <a name="a-namereleaserefa-releaseref"></a><a name="release_ref"></a>release_ref 

 当在派生类中重写，将释放对此的引用计数`ISource`块。  
  
```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 此方法由`ITarget`从此源要取消链接的对象。 源块允许释放任何资源为目标块保留。  
  
##  <a name="a-namereservea-reserve"></a><a name="reserve"></a>保留 

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
 `true`如果消息已成功保留，`false`否则为。 保留可能因为众多原因失败，包括：消息已保留或已由另一目标接受，源可能拒绝保留等。  
  
### <a name="remarks"></a>备注  
 在您调用之后`reserve`，如果成功，必须调用`consume`或`release`才能执行或分别放弃的消息的所有权。  
  
##  <a name="a-nameunlinktargeta-unlinktarget"></a><a name="unlink_target"></a>unlink_target 

 当在派生类中重写，将取消目标块与该链接`ISource`块，如果发现已链接。  
  
```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 要取消链接至此的目标块的指针`ISource`块。  
  
##  <a name="a-nameunlinktargetsa-unlinktargets"></a><a name="unlink_targets"></a>unlink_targets 

 当在派生类中重写，将取消所有目标块与该都链接`ISource`块。  
  
```
virtual void unlink_targets() = 0;
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ITarget 类](itarget-class.md)

