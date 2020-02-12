---
title: uninitialized_object 类
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: ef7ded0bf925d3430b70064c4979b75e08f9cf45
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127694"
---
# <a name="uninitialized_object-class"></a>uninitialized_object 类

当使用未初始化的对象时引发的异常。

## <a name="syntax"></a>语法

```cpp
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[uninitialized_object 构造函数](#uninitialized_object)|初始化 `uninitialized_object` 类的新实例。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>要求

**标头：** amprt

**命名空间：** 并发

## <a name="uninitialized_object"></a>uninitialized_object

构造 `uninitialized_object` 异常的新实例。

### <a name="syntax"></a>语法

```cpp
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误说明。

### <a name="return-value"></a>返回值

`uninitialized_object` exception 对象。

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
