---
title: invalid_scheduler_policy_thread_specification 类
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: b74439d1fca9ea990258ca5f7e36c865a2c49455
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491333"
---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification 类

此类描述尝试设置 `SchedulerPolicy` 对象的并发限制，以便 `MinConcurrency` 键的值小于 `MaxConcurrency` 键的值时引发的异常。

## <a name="syntax"></a>语法

```
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|已重载。 构造 `invalid_scheduler_policy_value` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发
##  <a name="ctor"></a> invalid_scheduler_policy_thread_specification

构造 `invalid_scheduler_policy_value` 对象。

```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[SchedulerPolicy 类](schedulerpolicy-class.md)
