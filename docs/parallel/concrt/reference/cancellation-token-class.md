---
title: "cancellation_token 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pplcancellation_token/concurrency::cancellation_token
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
caps.latest.revision: 10
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
ms.openlocfilehash: 93d5abe132203a53f3ffac8490fe32604e7e896e
ms.lasthandoff: 02/24/2017

---
# <a name="cancellationtoken-class"></a>cancellation_token 类
`cancellation_token` 类表示确定某项操作是否已请求取消的功能。 给定的标记可与 `task_group`、`structured_task_group` 或 `task` 关联以实现隐式取消。 它还可为了取消而进行轮询，或可在取消关联的 `cancellation_token_source` 时注册回调。  
  
## <a name="syntax"></a>语法  
  
```
class cancellation_token;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[cancellation_token 构造函数](#ctor)||  
|[~ cancellation_token 析构函数](#dtor)||  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[deregister_callback 方法](#deregister_callback)|通过 `register` 方法基于注册时返回的 `cancellation_token_registration` 对象移除之前注册的回调。|  
|[is_cancelable 方法](#is_cancelable)|返回有关此标记是否可取消的指示。|  
|[is_canceled 方法](#is_canceled)|如果标记已取消，则返回 `true`。|  
|[none 方法](#none)|返回一个取消标记，此标记绝不会受到取消。|  
|[register_callback 方法](#register_callback)|使用标记注册一个回调函数。 取消该标记时，将进行回调。 请注意，如果在调用此方法时已删除此标记，则将立即同步进行回调。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[运算符 ！ = 运算符](#operator_neq)||  
|[运算符 = 运算符](#operator_eq)||  
|[运算符 = = 运算符](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `cancellation_token`  
  
## <a name="requirements"></a>要求  
 **标头︰** pplcancellation_token.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namedtora-cancellationtoken"></a><a name="dtor"></a>~ cancellation_token 

```
~cancellation_token();
```  
  
##  <a name="a-namectora-cancellationtoken"></a><a name="ctor"></a>cancellation_token 

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>参数  
 `_Src`  
  
##  <a name="a-namederegistercallbacka-deregistercallback"></a><a name="deregister_callback"></a>deregister_callback 

 通过 `register` 方法基于注册时返回的 `cancellation_token_registration` 对象移除之前注册的回调。  
  
```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```  
  
### <a name="parameters"></a>参数  
 `_Registration`  
 与将取消注册的回调对应的 `cancellation_token_registration` 对象。 此标记必须先前已从对 `register` 的调用中返回。  
  
##  <a name="a-nameiscancelablea-iscancelable"></a><a name="is_cancelable"></a>is_cancelable 

 返回有关此标记是否可取消的指示。  
  
```
bool is_cancelable() const;
```  
  
### <a name="return-value"></a>返回值  
 有关此标记是否可以取消的指示。  
  
##  <a name="a-nameiscanceleda-iscanceled"></a><a name="is_canceled"></a>is_canceled 

 如果标记已取消，则返回 `true`。  
  
```
bool is_canceled() const;
```  
  
### <a name="return-value"></a>返回值  
 如果标记已取消，则值为 `true`；否则值为 `false`。  
  
##  <a name="a-namenonea-none"></a><a name="none"></a>无 

 返回一个取消标记，此标记绝不会受到取消。  
  
```
static cancellation_token none();
```  
  
### <a name="return-value"></a>返回值  
 无法取消的取消标记。  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>运算符 ！ = 

```
bool operator!= (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>参数  
 `_Src`  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>参数  
 `_Src`  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>运算符 = = 

```
bool operator== (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>参数  
 `_Src`  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-nameregistercallbacka-registercallback"></a><a name="register_callback"></a>register_callback 

 使用标记注册一个回调函数。 取消该标记时，将进行回调。 请注意，如果在调用此方法时已删除此标记，则将立即同步进行回调。  
  
```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 取消此 `cancellation_token` 时将回调的函数对象的类型。  
  
 `_Func`  
 取消此 `cancellation_token` 时将回调的函数对象。  
  
### <a name="return-value"></a>返回值  
 可在 `cancellation_token_registration` 方法中用于取消注册之前注册的回调并防止进行该回调的 `deregister` 对象。 该方法将引发[invalid_operation](invalid-operation-class.md)异常，如果它调用`cancellation_token`使用创建的对象[cancellation_token:: none](#none)方法。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

