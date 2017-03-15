---
title: "ITarget 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::ITarget
dev_langs:
- C++
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: 22
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
ms.openlocfilehash: aa9001de9ec35f20cd76f701d6b8acc5de7ffde0
ms.lasthandoff: 02/24/2017

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
 目标块可以接受的消息内负载的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|`filter_method`|返回的块使用任何方法的签名`bool`值以确定是否应接受提供的消息。|  
|`type`|类型别名`T`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[~ ITarget 析构函数](#dtor)|销毁`ITarget`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[propagate 方法](#propagate)|当在派生类中重写，以异步方式将消息传递从源块到此目标块。|  
|[send 方法](#send)|当在派生类中重写，以同步方式将消息传递到目标块。|  
|[supports_anonymous_source 方法](#supports_anonymous_source)|在派生类中重写时，根据消息块是否接受未链接到它的源提供的消息返回 true 或 false。 如果重写的方法返回 `true`，则目标不能推迟所提供的消息，因为稍后被推迟消息的能耗要求源在其源链接注册表中已标识。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[link_source 方法](#link_source)|当在派生类中重写，将指定的源块链接到此`ITarget`块。|  
|[unlink_source 方法](#unlink_source)|当在派生类中重写，将取消指定的源块与该链接`ITarget`块。|  
|[unlink_sources 方法](#unlink_sources)|当在派生类中重写，将取消所有源块与该都链接`ITarget`块。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ITarget`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namedtora-itarget"></a><a name="dtor"></a>~ ITarget 

 销毁`ITarget`对象。  
  
```
virtual ~ITarget();
```  
  
##  <a name="a-namelinksourcea-linksource"></a><a name="link_source"></a>link_source 

 当在派生类中重写，将指定的源块链接到此`ITarget`块。  
  
```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PSource`  
 `ISource`阻止被链接到此`ITarget`块。  
  
### <a name="remarks"></a>备注  
 不应直接调用此函数`ITarget`块。 应连接在一起使用的块`link_target`方法`ISource`块，将调用`link_source`相应目标系统上的方法。  
  
##  <a name="a-namepropagatea-propagate"></a><a name="propagate"></a>传播 

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
 一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果`_PMessage`或`_PSource`参数是`NULL`。  
  
##  <a name="a-namesenda-send"></a><a name="send"></a>发送 

 当在派生类中重写，以同步方式将消息传递到目标块。  
  
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
 一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果`_PMessage`或`_PSource`参数是`NULL`。  
  
 使用`send`消息初始化外并传播在网络中的消息的方法是危险的可能导致死锁。  
  
 当`send`返回时，该消息是已被接受，并传输到目标块后，或它已被拒绝的目标。  
  
##  <a name="a-namesupportsanonymoussourcea-supportsanonymoussource"></a><a name="supports_anonymous_source"></a>supports_anonymous_source 

 在派生类中重写时，根据消息块是否接受未链接到它的源提供的消息返回 true 或 false。 如果重写的方法返回 `true`，则目标不能推迟所提供的消息，因为稍后被推迟消息的能耗要求源在其源链接注册表中已标识。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>返回值  
 如果块可以接受来自未链接到它的源的消息，则为 `true`，否则为 `false`。  
  
##  <a name="a-nameunlinksourcea-unlinksource"></a><a name="unlink_source"></a>unlink_source 

 当在派生类中重写，将取消指定的源块与该链接`ITarget`块。  
  
```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PSource`  
 `ISource`阻止要取消链接至此`ITarget`块。  
  
### <a name="remarks"></a>备注  
 不应直接调用此函数`ITarget`块。 应使用断开连接块`unlink_target`或`unlink_targets`方法`ISource`块，将调用`unlink_source`相应目标系统上的方法。  
  
##  <a name="a-nameunlinksourcesa-unlinksources"></a><a name="unlink_sources"></a>unlink_sources 

 当在派生类中重写，将取消所有源块与该都链接`ITarget`块。  
  
```
virtual void unlink_sources() = 0;
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ISource 类](isource-class.md)

