---
title: unsupported_feature 类
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 7635f999b227d02ec7fd56296fef1b0b047abd29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405464"
---
# <a name="unsupportedfeature-class"></a>unsupported_feature 类

使用不支持的功能时引发的异常。

## <a name="syntax"></a>语法

```
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[unsupported_feature 构造函数](#unsupported_feature)|构造的新实例`unsupported_feature`异常。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupportedfeature"></a>unsupported_feature

  构造的新实例`unsupported_feature`异常。

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

## <a name="requirements"></a>要求

**标头：** amprt.h

**命名空间：** 并发

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
