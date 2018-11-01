---
title: context_self_unblock 类
ms.date: 11/04/2016
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
ms.openlocfilehash: 5cb7fc951a4c62f4d299ce7d394e9f8268d7ed74
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622165"
---
# <a name="contextselfunblock-class"></a>context_self_unblock 类

此类描述从同一上下文调用 `Context` 对象的 `Unblock` 方法时引发的异常。 这将指示给定上下文解除阻止自身的尝试。

## <a name="syntax"></a>语法

```
class context_self_unblock : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[context_self_unblock](#ctor)|已重载。 构造 `context_self_unblock` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`context_self_unblock`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> context_self_unblock

构造 `context_self_unblock` 对象。

```
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
