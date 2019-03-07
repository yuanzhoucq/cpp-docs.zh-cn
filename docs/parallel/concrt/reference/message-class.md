---
title: message 类
ms.date: 11/04/2016
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
ms.openlocfilehash: 83cfdb5807581f7092709691a1839052abdd657c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263073"
---
# <a name="message-class"></a>message 类

包含正在消息块之间传递的数据负载的基本消息信封。

## <a name="syntax"></a>语法

```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

#### <a name="parameters"></a>参数

*T*<br/>
在消息中的有效负载数据类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`type`|类型别名`T`。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[message](#ctor)|已重载。 构造 `message` 对象。|
|[~ message 析构函数](#dtor)|销毁`message`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[add_ref](#add_ref)|将添加到的引用计数`message`对象。 用于需要引用计数来确定消息生命周期的消息块。|
|[msg_id](#msg_id)|返回的 ID`message`对象。|
|[remove_ref](#remove_ref)|从的引用计数中减去`message`对象。 用于需要引用计数来确定消息生命周期的消息块。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[payload](#payload)|有效负载`message`对象。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`message`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="add_ref"></a> add_ref

将添加到的引用计数`message`对象。 用于需要引用计数来确定消息生命周期的消息块。

```
long add_ref();
```

### <a name="return-value"></a>返回值

新引用计数值。

##  <a name="ctor"></a> 消息

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

*_P*<br/>
此消息的负载。

*_Id*<br/>
此消息的唯一 ID。

*_Msg*<br/>
引用或指向`message`对象。

### <a name="remarks"></a>备注

将指针传递到构造函数`message`对象，如参数将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_Msg`是`NULL`。

##  <a name="dtor"></a> ~message

销毁`message`对象。

```
virtual ~message();
```

##  <a name="msg_id"></a> msg_id

返回的 ID`message`对象。

```
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>返回值

`runtime_object_identity`的`message`对象。

##  <a name="payload"></a> 有效负载

有效负载`message`对象。

```
T const payload;
```

##  <a name="remove_ref"></a> remove_ref

从的引用计数中减去`message`对象。 用于需要引用计数来确定消息生命周期的消息块。

```
long remove_ref();
```

### <a name="return-value"></a>返回值

新引用计数值。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
