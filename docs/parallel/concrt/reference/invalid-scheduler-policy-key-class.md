---
title: invalid_scheduler_policy_key 类
ms.date: 11/04/2016
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
ms.openlocfilehash: 1bc2f1cffdeba5f81bd96932ecef23a563fac351
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274058"
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key 类

此类描述无效或未知键传递给 `SchedulerPolicy` 对象构造函数，或 `SchedulerPolicy` 对象的 `SetPolicyValue` 方法被传递了必须使用其他方式（例如 `SetConcurrencyLimits` 方法）进行更改的键时引发的异常。

## <a name="syntax"></a>语法

```
class invalid_scheduler_policy_key : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[invalid_scheduler_policy_key](#ctor)|已重载。 构造 `invalid_scheduler_policy_key` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_scheduler_policy_key`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> invalid_scheduler_policy_key

构造 `invalid_scheduler_policy_key` 对象。

```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[SchedulerPolicy 类](schedulerpolicy-class.md)
