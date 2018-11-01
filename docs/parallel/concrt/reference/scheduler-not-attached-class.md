---
title: scheduler_not_attached 类
ms.date: 11/04/2016
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
ms.openlocfilehash: 159202445f95e8fbac93902dec43fc0f99180e8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560661"
---
# <a name="schedulernotattached-class"></a>scheduler_not_attached 类

此类描述需要将计划程序附加到当前上下文以执行操作，而实际并未进行附加即执行该操作时引发的异常。

## <a name="syntax"></a>语法

```
class scheduler_not_attached : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[scheduler_not_attached](#ctor)|已重载。 构造 `scheduler_not_attached` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`scheduler_not_attached`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> scheduler_not_attached

构造 `scheduler_not_attached` 对象。

```
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[Scheduler 类](scheduler-class.md)
