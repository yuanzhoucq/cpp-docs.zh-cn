---
title: default_scheduler_exists 类
ms.date: 11/04/2016
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
ms.openlocfilehash: eed5dd242beb4c4cd481f22635e0d5f71c28d7e6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139189"
---
# <a name="default_scheduler_exists-class"></a>default_scheduler_exists 类

此类描述在进程内已存在默认计划程序的情况下调用 `Scheduler::SetDefaultSchedulerPolicy` 方法时引发的异常。

## <a name="syntax"></a>语法

```cpp
class default_scheduler_exists : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[default_scheduler_exists](#ctor)|已重载。 构造 `default_scheduler_exists` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`default_scheduler_exists`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>default_scheduler_exists

构造 `default_scheduler_exists` 对象。

```cpp
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
