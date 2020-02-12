---
title: task_canceled 类
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: b1436f921343843ee2b50888f00b6d470e513329
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142607"
---
# <a name="task_canceled-class"></a>task_canceled 类

此类描述了 PPL 任务层为了强制取消当前任务而引发的异常。 对于已取消的任务，它还由[任务](/visualstudio/extensibility/debugger/task-class-internal-members)的 `get()` 方法引发。

## <a name="syntax"></a>语法

```cpp
class task_canceled : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[task_canceled](#ctor)|已重载。 构造 `task_canceled` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`task_canceled`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>task_canceled

构造 `task_canceled` 对象。

```cpp
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
