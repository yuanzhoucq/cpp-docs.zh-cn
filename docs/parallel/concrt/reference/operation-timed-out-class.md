---
title: operation_timed_out 类
ms.date: 11/04/2016
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
ms.openlocfilehash: 7a2513d30aa68798707f3bb16318db9b594b9e16
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138875"
---
# <a name="operation_timed_out-class"></a>operation_timed_out 类

此类描述操作超时时引发的异常。

## <a name="syntax"></a>语法

```cpp
class operation_timed_out : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[operation_timed_out](#ctor)|已重载。 构造 `operation_timed_out` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`operation_timed_out`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>operation_timed_out

构造 `operation_timed_out` 对象。

```cpp
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
