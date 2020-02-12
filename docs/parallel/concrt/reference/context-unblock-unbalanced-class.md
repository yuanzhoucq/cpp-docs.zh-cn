---
title: context_unblock_unbalanced 类
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: 261ec96c1a83fbec423e6dbbfe403c4db53a2962
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143099"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced 类

此类描述对 `Block` 对象的 `Unblock` 和 `Context` 方法的调用未恰当配对时引发的异常。

## <a name="syntax"></a>语法

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|已重载。 构造 `context_unblock_unbalanced` 对象。|

## <a name="remarks"></a>备注

对 `Context` 对象的 `Block` 和 `Unblock` 方法的调用必须始终正确配对。 并发运行时允许按照任意顺序执行操作。 例如，调用 `Block` 后可以调用 `Unblock`，反之亦然。 例如，如果在某个 `Context` 行中对 `Unblock` 方法发出了两次调用，则会引发此异常。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>context_unblock_unbalanced

构造 `context_unblock_unbalanced` 对象。

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
