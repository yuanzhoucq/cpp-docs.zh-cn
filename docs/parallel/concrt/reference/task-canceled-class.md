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
ms.openlocfilehash: caef1c62ff09ffb76f74d4a1453e9d59dcb7d45b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385240"
---
# <a name="taskcanceled-class"></a>task_canceled 类

此类描述了 PPL 任务层为了强制取消当前任务而引发的异常。 它也会通过引发`get()`方法[任务](/visualstudio/extensibility/debugger/task-class-internal-members)，为已取消的任务。

## <a name="syntax"></a>语法

```
class task_canceled : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[task_canceled](#ctor)|已重载。 构造 `task_canceled` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`task_canceled`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> task_canceled

构造 `task_canceled` 对象。

```
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
