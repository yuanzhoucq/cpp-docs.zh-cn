---
title: "message 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::message
dev_langs:
- C++
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
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
ms.openlocfilehash: 08d67f2899f27a92250d6fedbf755a5413e01ebd
ms.lasthandoff: 02/24/2017

---
# <a name="message-class"></a>message 类
包含正在消息块之间传递的数据负载的基本消息信封。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 消息中的负载的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`type`|类型别名`T`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[消息构造函数](#ctor)|已重载。 构造 `message` 对象。|  
|[~ message 析构函数](#dtor)|销毁`message`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[add_ref 方法](#add_ref)|将添加到的引用计数`message`对象。 用于需要引用计数以确定消息生存期的消息块。|  
|[msg_id 方法](#msg_id)|返回的 ID`message`对象。|  
|[remove_ref 方法](#remove_ref)|将从的引用计数中减去`message`对象。 用于需要引用计数以确定消息生存期的消息块。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[负载数据成员](#payload)|有效负载`message`对象。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `message`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameaddrefa-addref"></a><a name="add_ref"></a>add_ref 

 将添加到的引用计数`message`对象。 用于需要引用计数以确定消息生存期的消息块。  
  
```
long add_ref();
```  
  
### <a name="return-value"></a>返回值  
 新的引用计数值。  
  
##  <a name="a-namectora-message"></a><a name="ctor"></a>消息 

 构造 `message` 对象。  
  
```
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```  
  
### <a name="parameters"></a>参数  
 `_P`  
 此消息的负载。  
  
 `_Id`  
 此消息的唯一 ID。  
  
 `_Msg`  
 一个引用或指针，指向`message`对象。  
  
### <a name="remarks"></a>备注  
 构造函数来采用一个指向`message`对象作为参数将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_Msg`是`NULL`。  
  
##  <a name="a-namedtora-message"></a><a name="dtor"></a>~ 消息 

 销毁`message`对象。  
  
```
virtual ~message();
```  
  
##  <a name="a-namemsgida-msgid"></a><a name="msg_id"></a>msg_id 

 返回的 ID`message`对象。  
  
```
runtime_object_identity msg_id() const;
```  
  
### <a name="return-value"></a>返回值  
 `runtime_object_identity`的`message`对象。  
  
##  <a name="a-namepayloada-payload"></a><a name="payload"></a>有效负载 

 有效负载`message`对象。  
  
```
T const payload;
```  
  
##  <a name="a-nameremoverefa-removeref"></a><a name="remove_ref"></a>remove_ref 

 将从的引用计数中减去`message`对象。 用于需要引用计数以确定消息生存期的消息块。  
  
```
long remove_ref();
```  
  
### <a name="return-value"></a>返回值  
 新的引用计数值。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

