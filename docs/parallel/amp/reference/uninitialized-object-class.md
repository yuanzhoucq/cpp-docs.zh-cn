---
title: uninitialized_object 类
ms.date: 11/04/2016
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: 1c431364aee0f1d1e75059abdb023ae52cf92155
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279324"
---
# <a name="uninitializedobject-class"></a>uninitialized_object 类

使用未初始化的对象时引发的异常。

## <a name="syntax"></a>语法

```
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[uninitialized_object 构造函数](#ctor)|初始化 `uninitialized_object` 类的新实例。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>要求

**标头：** amprt.h

**命名空间：** 并发
## <a name="uninitialized_object__ctor"></a> unsupported_feature

构造的功能异常的新实例。

### <a name="syntax"></a>语法

```
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误说明。

### <a name="return-value"></a>返回值

`unsupported_feature` 对象。

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
