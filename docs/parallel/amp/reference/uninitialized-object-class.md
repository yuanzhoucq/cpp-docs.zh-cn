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
ms.openlocfilehash: 05c24672531d50fa9bc31587e6c6733fdff21f29
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565529"
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
|[uninitialized_object 构造函数](#uninitialized_object)|初始化 `uninitialized_object` 类的新实例。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>要求

**标头：** amprt.h

**命名空间：** 并发

## <a name="uninitializedobject"></a>uninitialized_object

构造的新实例`uninitialized_object`异常。

### <a name="syntax"></a>语法

```
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误说明。

### <a name="return-value"></a>返回值

`uninitialized_object`异常对象。

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
