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
ms.openlocfilehash: aa22c9b218b88a8834e8ba474c2aa2c203ea89dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517112"
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling 类

此类描述在没有对 `wait` 或 `run_and_wait` 方法进行干预调用的情况下，通过 `task_group` 或 `structured_task_group` 对象的 `run` 方法对 `task_handle` 对象进行多次计划时引发的异常。

## <a name="syntax"></a>语法

```
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|已重载。 构造 `invalid_multiple_scheduling` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> invalid_multiple_scheduling

构造 `invalid_multiple_scheduling` 对象。

```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[task_handle 类](task-handle-class.md)<br/>
[task_group 类](task-group-class.md)<br/>
[run](task-group-class.md)<br/>
[等待](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group 类](structured-task-group-class.md)
