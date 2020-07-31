---
title: task_completion_event 类
ms.date: 11/04/2016
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
ms.openlocfilehash: b63e8c6986508806cedc8c094a4e8844491dd2fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219503"
---
# <a name="task_completion_event-class"></a>task_completion_event 类

`task_completion_event` 类可让你延迟任务的执行，直到满足条件，或开始一项任务来响应外部事件。

## <a name="syntax"></a>语法

```cpp
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

### <a name="parameters"></a>参数

*_ResultType*<br/>
此 `task_completion_event` 类的结果类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[task_completion_event](#ctor)|构造 `task_completion_event` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[set](#set)|已重载。 设置任务完成事件。|
|[set_exception](#set_exception)|已重载。 传播与此事件关联的所有任务的一个例外情况。|

## <a name="remarks"></a>备注

在你的方案要求创建将完成的任务时使用基于任务完成事件创建的任务，从而计划在将来的某个时候执行其延续。 `task_completion_event` 的类型必须与创建的任务的类型相同，而对包含该类型的值的任务完成事件调用 set 方法将导致关联的任务完成，并提供该值作为其延续的结果。

如果任务完成事件始终未收到信号，则当它被销毁时，基于它创建的任何任务都将被取消。

`task_completion_event` 的行为类似于能指针，并应按值传递。

## <a name="inheritance-hierarchy"></a>继承层次结构

`task_completion_event`

## <a name="requirements"></a>要求

**标头：** ppltasks。h

**命名空间：** 并发

## <a name="set"></a><a name="set"></a>字符集

设置任务完成事件。

```cpp
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>参数

*_Result*<br/>
要为其设置此事件的结果。

### <a name="return-value"></a>返回值

**`true`** 如果它成功设置了事件，则该方法将返回。 **`false`** 如果已设置该事件，则返回。

### <a name="remarks"></a>备注

如果存在多个或并发调用，则 `set` 只有第一个调用将成功，并且其结果（如果有）将存储在任务完成事件中。 剩余的集被忽略，并且方法将返回 false。 设置任务完成事件时，从该事件创建的所有任务都将立即完成，并将计划其延续任务（如果有）。 除之外的任务完成对象 `_ResultType` **`void`** 将值传递给其延续。

## <a name="set_exception"></a><a name="set_exception"></a>set_exception

传播与此事件关联的所有任务的一个例外情况。

```cpp
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>参数

*_E*<br/>
异常类型。

*_Except*<br/>
要设置的异常。

*_ExceptionPtr*<br/>
要设置的异常指针。

### <a name="return-value"></a>返回值

## <a name="task_completion_event"></a><a name="ctor"></a>task_completion_event

构造 `task_completion_event` 对象。

```cpp
task_completion_event();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
