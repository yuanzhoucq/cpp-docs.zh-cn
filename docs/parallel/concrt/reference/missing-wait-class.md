---
title: missing_wait 类
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: cf81d1ee6c144da210da5b1f37aca7910ae37bc8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142378"
---
# <a name="missing_wait-class"></a>missing_wait 类

此类描述执行对象的析构函数时仍有计划到 `task_group` 或 `structured_task_group` 对象的任务时引发的异常。 如果因为堆栈展开为异常的结果而到达析构函数的调用条件，则永远不会引发此异常。

## <a name="syntax"></a>语法

```cpp
class missing_wait : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[missing_wait](#ctor)|已重载。 构造 `missing_wait` 对象。|

## <a name="remarks"></a>备注

缺少异常流，你负责在允许该对象销毁之前，调用 `task_group` 或 `structured_task_group` 对象的 `wait` 或 `run_and_wait` 方法。 运行时引发此异常，表示你忘记调用 `wait` 或 `run_and_wait` 方法。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`missing_wait`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>missing_wait

构造 `missing_wait` 对象。

```cpp
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[task_group 类](task-group-class.md)<br/>
[再](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group 类](structured-task-group-class.md)
