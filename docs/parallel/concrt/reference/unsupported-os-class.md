---
title: unsupported_os 类
ms.date: 11/04/2016
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
ms.openlocfilehash: 8277827aa8713ef57731a3e0da0898829b9fa9fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186359"
---
# <a name="unsupportedos-class"></a>unsupported_os 类

此类描述使用不受支持的操作系统时引发的一种异常。

## <a name="syntax"></a>语法

```
class unsupported_os : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[unsupported_os](#ctor)|已重载。 构造 `unsupported_os` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`unsupported_os`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> unsupported_os

构造 `unsupported_os` 对象。

```
explicit _CRTIMP unsupported_os(_In_z_ const char* _Message) throw();

unsupported_os() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
