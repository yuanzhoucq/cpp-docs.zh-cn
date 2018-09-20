---
title: cancellation_token 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9b438725a5a725597a81f0587936618a06cbb4b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414298"
---
# <a name="cancellationtoken-class"></a>cancellation_token 类

`cancellation_token` 类表示确定某项操作是否已请求取消的功能。 给定的标记可与 `task_group`、`structured_task_group` 或 `task` 关联以实现隐式取消。 它还可为了取消而进行轮询，或可在取消关联的 `cancellation_token_source` 时注册回调。

## <a name="syntax"></a>语法

```
class cancellation_token;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[~ cancellation_token 析构函数](#dtor)||

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|通过 `register` 方法基于注册时返回的 `cancellation_token_registration` 对象移除之前注册的回调。|
|[is_cancelable](#is_cancelable)|返回有关此标记是否可取消的指示。|
|[is_canceled](#is_canceled)|如果标记已取消，则返回 `true`。|
|[none](#none)|返回一个取消标记，此标记绝不会受到取消。|
|[register_callback](#register_callback)|使用标记注册一个回调函数。 取消该标记时，将进行回调。 请注意，如果在调用此方法时已删除此标记，则将立即同步进行回调。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`cancellation_token`

## <a name="requirements"></a>要求

**标头：** pplcancellation_token.h

**命名空间：** 并发

##  <a name="dtor"></a> ~ cancellation_token

```
~cancellation_token();
```

##  <a name="ctor"></a> cancellation_token

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>参数

*_Src*<br/>
要复制或移动 cancellation_token。

##  <a name="deregister_callback"></a> deregister_callback

通过 `register` 方法基于注册时返回的 `cancellation_token_registration` 对象移除之前注册的回调。

```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>参数

*_Registration*<br/>
与将取消注册的回调对应的 `cancellation_token_registration` 对象。 此标记必须先前已从对 `register` 的调用中返回。

##  <a name="is_cancelable"></a> is_cancelable

返回有关此标记是否可取消的指示。

```
bool is_cancelable() const;
```

### <a name="return-value"></a>返回值

有关此标记是否可以取消的指示。

##  <a name="is_canceled"></a> is_canceled

如果标记已取消，则返回 `true`。

```
bool is_canceled() const;
```

### <a name="return-value"></a>返回值

如果标记已取消，则值为 `true`；否则值为 `false`。

##  <a name="none"></a> 无

返回一个取消标记，此标记绝不会受到取消。

```
static cancellation_token none();
```

### <a name="return-value"></a>返回值

无法取消的取消标记。

##  <a name="operator_neq"></a> 运算符 ！ =

```
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>参数

*_Src*<br/>
要比较的 `cancellation_token`。

### <a name="return-value"></a>返回值

##  <a name="operator_eq"></a> 运算符 =

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>参数

*_Src*<br/>
`cancellation_token`分配。

### <a name="return-value"></a>返回值

##  <a name="operator_eq_eq"></a> 运算符 = =

```
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>参数

*_Src*<br/>
要比较的 `cancellation_token`。

### <a name="return-value"></a>返回值

##  <a name="register_callback"></a> register_callback

使用标记注册一个回调函数。 取消该标记时，将进行回调。 请注意，如果在调用此方法时已删除此标记，则将立即同步进行回调。

```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>参数

*_Function*<br/>
取消此 `cancellation_token` 时将回调的函数对象的类型。

*_Func*<br/>
取消此 `cancellation_token` 时将回调的函数对象。

### <a name="return-value"></a>返回值

可在 `cancellation_token_registration` 方法中用于取消注册之前注册的回调并防止进行该回调的 `deregister` 对象。 该方法将引发[invalid_operation](invalid-operation-class.md)异常，如果在调用`cancellation_token`使用创建的对象[cancellation_token:: none](#none)方法。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
