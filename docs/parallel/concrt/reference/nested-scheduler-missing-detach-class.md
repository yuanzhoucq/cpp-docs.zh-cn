---
title: nested_scheduler_missing_detach 类
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: db51f7b083cc0cbd9337fbbe5c672d190208f328
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394385"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach 类

此类描述并发运行时检测到你没有在通过 `Scheduler` 对象的 `Attach` 方法附加到第二个计划程序的上下文中调用 `CurrentScheduler::Detach` 方法时引发的异常。

## <a name="syntax"></a>语法

```
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|已重载。 构造 `nested_scheduler_missing_detach` 对象。|

## <a name="remarks"></a>备注

仅当在另一个计划程序中嵌套计划程序，方法为在已由另一计划程序拥有或连接至另一计划程序的上下文中调用 `Attach` 对象的 `Scheduler` 方法时，才会引发该异常。 并发运行时引发此异常时它可以检测方案作为查找问题的辅助手段。 忘记调用不是每个实例`CurrentScheduler::Detach`方法肯定会引发此异常。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> nested_scheduler_missing_detach

构造 `nested_scheduler_missing_detach` 对象。

```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[Scheduler 类](scheduler-class.md)
