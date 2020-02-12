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
ms.openlocfilehash: 883d5630251a6ea13afba1164f221a0da1773c17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143116"
---
# <a name="context_self_unblock-class"></a>context_self_unblock 类

此类描述从同一上下文调用 `Unblock` 对象的 `Context` 方法时引发的异常。 这将指示给定上下文解除阻止自身的尝试。

## <a name="syntax"></a>语法

```cpp
class context_self_unblock : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[context_self_unblock](#ctor)|已重载。 构造 `context_self_unblock` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`context_self_unblock`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>context_self_unblock

构造 `context_self_unblock` 对象。

```cpp
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
