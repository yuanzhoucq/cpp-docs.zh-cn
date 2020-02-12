---
title: task_continuation_context 类
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: ae8ac425f035839cdddc0b19f4f40d3b6369202a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142578"
---
# <a name="task_continuation_context-class"></a>task_continuation_context 类

`task_continuation_context` 类可让你指定想要执行延续的位置。 仅在 Windows 运行时应用中使用此类时才有用。 对于非 Windows 运行时应用，任务延续的执行上下文由运行时确定，并且不可配置。

## <a name="syntax"></a>语法

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|返回表示当前 winrt 线程上下文的任务延续上下文对象。|
|[use_arbitrary](#use_arbitrary)|创建允许运行时选择延续的执行上下文的任务延续上下文。|
|[use_current](#use_current)|返回表示当前执行上下文的任务延续上下文对象。|
|[use_default](#use_default)|创建默认任务延续上下文。|
|[use_synchronous_execution](#use_synchronous_execution)|返回表示同步执行上下文的任务延续上下文对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>要求

**标头：** ppltasks。h

**命名空间：** 并发

## <a name="get_current_winrt_context"></a>get_current_winrt_context

返回表示当前 WinRT 线程上下文的任务延续上下文对象。

### <a name="syntax"></a>语法

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>返回值

当前 Windows 运行时线程上下文。 如果从非 Windows 运行时上下文中调用，则返回空 task_continuation_context。

### <a name="remarks"></a>备注

`get_current_winrt_context` 方法捕获调用方的 Windows 运行时线程上下文。 它将向非 Windows 运行时调用方返回一个空的上下文。

`get_current_winrt_context` 返回的值可用于向运行时指示延续应在捕获的上下文（STA vs MTA）的单元模型中执行，而不考虑前面的任务是否是单元感知。 单元识别任务是一种将 Windows 运行时 `IAsyncInfo` 接口或从这类任务继承的任务的任务。

此方法类似于 `use_current` 方法，但它也适用于没有C++ C++/cx 扩展支持的本机代码。 它旨在供高级用户使用，用于为C++本机和 Windows 运行时调用方编写/CX-agnostic 库代码。 除非需要此功能，否则建议仅向C++/cx 客户端提供 `use_current` 方法。

## <a name="use_arbitrary"></a>use_arbitrary

创建允许运行时选择延续的执行上下文的任务延续上下文。

### <a name="syntax"></a>语法

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>返回值

表示任意位置的任务延续上下文。

### <a name="remarks"></a>备注

使用此延续上下文时，延续将在运行时选择的上下文中执行，即使前面的任务是单元感知也是如此。

`use_arbitrary` 可用于关闭在 STA 中创建的单元感知任务的默认行为。

此方法仅可用于 Windows 运行时应用。

## <a name="use_current"></a>use_current

返回表示当前执行上下文的任务延续上下文对象。

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>返回值

当前执行上下文。

### <a name="remarks"></a>备注

此方法捕获调用方的 Windows 运行时上下文，以便可在右单元中执行延续任务。

`use_current` 返回的值可用于向运行时指示，无论前面的任务是否都是单元感知，延续都应在捕获的上下文（STA 与 MTA）中执行。 单元识别任务是一种将 Windows 运行时 `IAsyncInfo` 接口或从这类任务继承的任务的任务。

此方法仅可用于 Windows 运行时应用。

## <a name="use_default"></a>use_default

创建默认任务延续上下文。

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>返回值

默认延续上下文。

### <a name="remarks"></a>备注

如果在调用 `then` 方法时未指定继续上下文，则使用默认上下文。 在 windows 7 及更高版本的 Windows 应用程序以及 Windows 8 及更高版本上的桌面应用程序中，运行时确定任务继续执行的位置。 但是，在 Windows 运行时应用程序中，可在单元识别任务上继续执行的默认延续上下文是调用 `then` 的单元。

单元识别任务是一种将 Windows 运行时 `IAsyncInfo` 接口或从这类任务继承的任务的任务。 因此，如果在 Windows 运行时 STA 中的单元感知任务上计划继续，则延续任务将在该 STA 中执行。

非单元识别任务上的延续将在运行时选择的上下文中执行。

## <a name="use_synchronous_execution"></a>task_continuation_context：： use_synchronous_execution

返回表示同步执行上下文的任务延续上下文对象。

### <a name="syntax"></a>语法

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>返回值

同步执行上下文。

### <a name="remarks"></a>备注

`use_synchronous_execution` 方法强制延续任务在上下文上同步运行，从而导致其任务完成。

如果在附加延续后前面的任务已完成，则延续将在附加延续的上下文中同步运行。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
