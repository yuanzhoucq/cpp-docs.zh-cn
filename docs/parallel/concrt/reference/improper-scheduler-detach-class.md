---
title: improper_scheduler_detach 类
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach::improper_scheduler_detach
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
ms.openlocfilehash: b2fc90656051be62528d0aac600fad67485c81f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643282"
---
# <a name="improperschedulerdetach-class"></a>improper_scheduler_detach 类

此类描述在尚未附加到任何使用 `Scheduler` 对象的 `Attach` 方法的计划程序的上下文中调用 `CurrentScheduler::Detach` 方法时引发的异常。

## <a name="syntax"></a>语法

```
class improper_scheduler_detach : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[improper_scheduler_detach](#ctor)|已重载。 构造 `improper_scheduler_detach` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`improper_scheduler_detach`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> improper_scheduler_detach

构造 `improper_scheduler_detach` 对象。

```
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[Scheduler 类](scheduler-class.md)
