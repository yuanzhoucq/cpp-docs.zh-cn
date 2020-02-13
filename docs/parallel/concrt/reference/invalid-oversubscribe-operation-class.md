---
title: invalid_oversubscribe_operation 类
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 7a879fc2da2f963cd4b5ea5fcd7e9506f86ce051
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140835"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation 类

此类描述在以下情况下引发的异常：在调用 `Context::Oversubscribe` 方法时，如果 `_BeginOversubscription` 参数设置为**false** ，则不会调用 `Context::Oversubscribe` 方法，并将 `_BeginOversubscription` 参数设置为**true**。

## <a name="syntax"></a>语法

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|已重载。 构造 `invalid_oversubscribe_operation` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>invalid_oversubscribe_operation

构造 `invalid_oversubscribe_operation` 对象。

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
