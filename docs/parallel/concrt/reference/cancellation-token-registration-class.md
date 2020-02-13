---
title: cancellation_token_registration 类
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: 9342841e207c93b66521c2fc742c1b1114682f78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142239"
---
# <a name="cancellation_token_registration-class"></a>cancellation_token_registration 类

`cancellation_token_registration` 类表示来自 `cancellation_token` 的回调通知。 如果 `register` 上的 `cancellation_token` 方法用于接收何时进行取消的通知，则系统就会将 `cancellation_token_registration` 对象作为回调的句柄返回，以便调用方可以请求特定回调，而不再通过使用 `deregister` 方法来实现。

## <a name="syntax"></a>语法

```cpp
class cancellation_token_registration;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration 析构函数](#dtor)||

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`cancellation_token_registration`

## <a name="requirements"></a>要求

**标头：** pplcancellation_token。h

**命名空间：** 并发

## <a name="dtor"></a>~ cancellation_token_registration

```cpp
~cancellation_token_registration();
```

## <a name="ctor"></a>cancellation_token_registration

```cpp
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>参数

*_Src*<br/>
要复制或移动的 `cancellation_token_registration`。

## <a name="operator_neq"></a>operator！ =

```cpp
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要比较的 `cancellation_token_registration`。

### <a name="return-value"></a>返回值

## <a name="operator_eq"></a>operator =

```cpp
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>参数

*_Src*<br/>
要分配的 `cancellation_token_registration`。

### <a name="return-value"></a>返回值

## <a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要比较的 `cancellation_token_registration`。

### <a name="return-value"></a>返回值

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
