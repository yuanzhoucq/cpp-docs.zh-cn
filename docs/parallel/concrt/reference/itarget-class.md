---
title: ITarget 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9780e4b9ff8950511601b03e8423764c3def77a1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691485"
---
# <a name="itarget-class"></a>ITarget 类
`ITarget` 类是所有目标块的接口。 目标块使用 `ISource` 块提供给它们的消息。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class ITarget;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 目标块接受的消息中的负载的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`filter_method`|返回的块使用任何方法的签名`bool`值以确定是否应接受提供的消息。|  
|`type`|类型别名`T`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[~ ITarget 析构函数](#dtor)|销毁`ITarget`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[propagate](#propagate)|当在派生类中重写，以异步方式将消息传递从源块到此目标块。|  
|[发送](#send)|当在派生类中重写，以同步方式将消息传递给目标块。|  
|[supports_anonymous_source](#supports_anonymous_source)|在派生类中重写时，根据消息块是否接受未链接到它的源提供的消息返回 true 或 false。 如果重写的方法返回 `true`，则目标不能推迟所提供的消息，因为稍后被推迟消息的能耗要求源在其源链接注册表中已标识。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[link_source](#link_source)|当在派生类中重写，将指定的源块链接到此`ITarget`块。|  
|[unlink_source](#unlink_source)|当在派生类中重写，传递指定的源块与该取消链接`ITarget`块。|  
|[unlink_sources](#unlink_sources)|当在派生类中重写，传递取消链接所有源块与该`ITarget`块。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ITarget`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="dtor"></a> ~ ITarget 

 销毁`ITarget`对象。  
  
```
virtual ~ITarget();
```  
  
##  <a name="link_source"></a> link_source 

 当在派生类中重写，将指定的源块链接到此`ITarget`块。  
  
```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PSource`  
 `ISource`阻止被链接到此`ITarget`块。  
  
### <a name="remarks"></a>备注  
 不应直接在上调用此函数`ITarget`块。 应连接在一起使用的块`link_target`方法`ISource`块，将调用`link_source`相应目标上的方法。  
  
##  <a name="propagate"></a> 传播 

 当在派生类中重写，以异步方式将消息传递从源块到此目标块。  
  
```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果`_PMessage`或`_PSource`参数是`NULL`。  
  
##  <a name="send"></a> 发送 

 当在派生类中重写，以同步方式将消息传递给目标块。  
  
```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果`_PMessage`或`_PSource`参数是`NULL`。  
  
 使用`send`方法之外消息启动并传播在网络中的消息是危险的可能会导致死锁。  
  
 当`send`返回时，消息是已被接受，并传输到目标块，或它已被拒绝由目标。  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 在派生类中重写时，根据消息块是否接受未链接到它的源提供的消息返回 true 或 false。 如果重写的方法返回 `true`，则目标不能推迟所提供的消息，因为稍后被推迟消息的能耗要求源在其源链接注册表中已标识。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>返回值  
 如果块可以接受来自未链接到它的源的消息，则为 `true`，否则为 `false`。  
  
##  <a name="unlink_source"></a> unlink_source 

 当在派生类中重写，传递指定的源块与该取消链接`ITarget`块。  
  
```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PSource`  
 `ISource`阻止要取消链接至此`ITarget`块。  
  
### <a name="remarks"></a>备注  
 不应直接在上调用此函数`ITarget`块。 应使用断开连接块`unlink_target`或`unlink_targets`方法`ISource`块，将调用`unlink_source`相应目标上的方法。  
  
##  <a name="unlink_sources"></a> unlink_sources 

 当在派生类中重写，传递取消链接所有源块与该`ITarget`块。  
  
```
virtual void unlink_sources() = 0;
```  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ISource 类](isource-class.md)
