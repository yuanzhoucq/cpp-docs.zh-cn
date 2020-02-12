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
ms.openlocfilehash: 700d052b6f22c970387a3ab45d299538a5b74e1b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139533"
---
# <a name="message-class"></a>message 类

包含正在消息块之间传递的数据负载的基本消息信封。

## <a name="syntax"></a>语法

```cpp
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

### <a name="parameters"></a>参数

*T*<br/>
消息内有效负载的数据类型。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|name|描述|
|----------|-----------------|
|`type`|`T`的类型别名。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[message](#ctor)|已重载。 构造 `message` 对象。|
|[~ 消息析构函数](#dtor)|销毁 `message` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[add_ref](#add_ref)|添加到 `message` 对象的引用计数。 用于需要引用计数来确定消息生存期的消息块。|
|[msg_id](#msg_id)|返回 `message` 对象的 ID。|
|[remove_ref](#remove_ref)|从 `message` 对象的引用计数中减去。 用于需要引用计数来确定消息生存期的消息块。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[payload](#payload)|`message` 对象的负载。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`message`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="add_ref"></a> add_ref

添加到 `message` 对象的引用计数。 用于需要引用计数来确定消息生存期的消息块。

```cpp
long add_ref();
```

### <a name="return-value"></a>返回值

引用计数的新值。

## <a name="ctor"></a>消息

构造 `message` 对象。

```cpp
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
此消息的有效负载。

*_Id*<br/>
此消息的唯一 ID。

*_Msg*<br/>
指向 `message` 对象的引用或指针。

### <a name="remarks"></a>备注

如果 `NULL``_Msg` 参数，则采用作为参数的 `message` 对象的指针的构造函数将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

## <a name="dtor"></a>~ 消息

销毁 `message` 的对象。

```cpp
virtual ~message();
```

## <a name="msg_id"></a> msg_id

返回 `message` 对象的 ID。

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>返回值

`runtime_object_identity` 对象的 `message`。

## <a name="payload"></a>负载

`message` 对象的负载。

```cpp
T const payload;
```

## <a name="remove_ref"></a>remove_ref

从 `message` 对象的引用计数中减去。 用于需要引用计数来确定消息生存期的消息块。

```cpp
long remove_ref();
```

### <a name="return-value"></a>返回值

引用计数的新值。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
