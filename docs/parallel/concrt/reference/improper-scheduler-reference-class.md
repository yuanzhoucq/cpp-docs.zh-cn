---
title: improper_scheduler_reference 类
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
ms.openlocfilehash: 9bb62fbf5048766d2d11f344a401979e107ec702
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597179"
---
# <a name="improperschedulerreference-class"></a>improper_scheduler_reference 类

此类描述从不属于该计划程序的上下文中，在正在关闭的 `Scheduler` 对象上调用 `Reference` 方法时引发的异常。

## <a name="syntax"></a>语法

```
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|已重载。 构造 `improper_scheduler_reference` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> improper_scheduler_reference

构造 `improper_scheduler_reference` 对象。

```
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[Scheduler 类](scheduler-class.md)
