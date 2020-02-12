---
title: invalid_multiple_scheduling 类
ms.date: 11/04/2016
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
ms.openlocfilehash: a8b2a045ce94562dcba0019bc03aaa90c4d384a9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140904"
---
# <a name="invalid_multiple_scheduling-class"></a>invalid_multiple_scheduling 类

此类描述在没有对 `task_handle` 或 `run` 方法进行干预调用的情况下，通过 `task_group` 或 `structured_task_group` 对象的 `wait` 方法对 `run_and_wait` 对象进行多次计划时引发的异常。

## <a name="syntax"></a>语法

```cpp
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|已重载。 构造 `invalid_multiple_scheduling` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>invalid_multiple_scheduling

构造 `invalid_multiple_scheduling` 对象。

```cpp
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[task_handle 类](task-handle-class.md)<br/>
[task_group 类](task-group-class.md)<br/>
[run](task-group-class.md)<br/>
[再](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group 类](structured-task-group-class.md)
