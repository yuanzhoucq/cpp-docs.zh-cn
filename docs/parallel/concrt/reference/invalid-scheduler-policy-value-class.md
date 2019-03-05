---
title: invalid_scheduler_policy_value 类
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
ms.openlocfilehash: 8b8e233769d859aac102d0554a6987e9b7201473
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301436"
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value 类

此类描述 `SchedulerPolicy` 对象的策略键设置为对于该键无效的值时引发的异常。

## <a name="syntax"></a>语法

```
class invalid_scheduler_policy_value : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|已重载。 构造 `invalid_scheduler_policy_value` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_scheduler_policy_value`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> invalid_scheduler_policy_value

构造 `invalid_scheduler_policy_value` 对象。

```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[SchedulerPolicy 类](schedulerpolicy-class.md)
