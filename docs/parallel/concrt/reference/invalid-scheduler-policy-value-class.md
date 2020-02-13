---
title: invalid_scheduler_policy_value Class类
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
ms.openlocfilehash: 6a66b2b303a4b3b0cb8c2c7a3c515ac8cd1b33a0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142994"
---
# <a name="invalid_scheduler_policy_value-class"></a>invalid_scheduler_policy_value Class类

此类描述 `SchedulerPolicy` 对象的策略键设置为对于该键无效的值时引发的异常。

## <a name="syntax"></a>语法

```cpp
class invalid_scheduler_policy_value : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|已重载。 构造 `invalid_scheduler_policy_value` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_scheduler_policy_value`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>invalid_scheduler_policy_value

构造 `invalid_scheduler_policy_value` 对象。

```cpp
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[SchedulerPolicy 类](schedulerpolicy-class.md)
