---
title: context_unblock_unbalanced 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
dev_langs:
- C++
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cd35b53db37d51a9feec567fe66c53b1381b4d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431328"
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced 类

此类描述对 `Context` 对象的 `Block` 和 `Unblock` 方法的调用未恰当配对时引发的异常。

## <a name="syntax"></a>语法

```
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|已重载。 构造 `context_unblock_unbalanced` 对象。|

## <a name="remarks"></a>备注

调用`Block`并`Unblock`方法的`Context`对象必须始终正确配对。 并发运行时允许按任意顺序发生的操作。 例如，调用 `Block` 后可以调用 `Unblock`，反之亦然。 如果，例如，两次调用将引发此异常`Unblock`方法执行了某行中，`Context`对象不被阻止。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> context_unblock_unbalanced

构造 `context_unblock_unbalanced` 对象。

```
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
