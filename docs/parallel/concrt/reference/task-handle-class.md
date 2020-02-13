---
title: task_handle 类
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: a61e72f14448d5033d5be9069ffeec7d3bb08061
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142555"
---
# <a name="task_handle-class"></a>task_handle 类

`task_handle` 类表示单个并行工作项。 它封装执行一项工作所需的指令和数据。

## <a name="syntax"></a>语法

```cpp
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

### <a name="parameters"></a>参数

*_Function*<br/>
函数对象的类型，将调用该函数对象来执行由 `task_handle` 对象表示的工作。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[task_handle](#task_handle)|构造新的 `task_handle` 对象。 任务的工作是通过调用指定为构造函数的参数的函数来执行的。|
|[~ task_handle 析构函数](#dtor)|销毁 `task_handle` 的对象。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|运行时调用以执行任务句柄工作的函数调用运算符。|

## <a name="remarks"></a>备注

`task_handle` 对象可以与 `structured_task_group` 或更通用的 `task_group` 对象结合使用，以便将工作分解为并行任务。 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

请注意，`task_handle` 对象的创建者负责维护创建的 `task_handle` 对象的生存期，直到并发运行时不再需要它。 通常，这意味着 `task_handle` 对象在被调用的 `task_group` 或 `structured_task_group` 的 `wait` 或 `run_and_wait` 方法被调用之前，不能析构。

`task_handle` 对象通常与C++ lambda 一起使用。 由于你不知道 lambda 的真正类型，因此[make_task](concurrency-namespace-functions.md#make_task)函数通常用于创建 `task_handle` 对象。

运行时创建您传递到 `task_handle` 对象的工作函数的副本。 因此，传递到 `task_handle` 对象的函数对象中发生的任何状态更改都不会出现在该函数对象的副本中。

## <a name="inheritance-hierarchy"></a>继承层次结构

`task_handle`

## <a name="requirements"></a>要求

**标头：** ppl。h

**命名空间：** 并发

## <a name="task_handle__operator_call"></a>operator （）

运行时调用以执行任务句柄工作的函数调用运算符。

```cpp
void operator()() const;
```

## <a name="task_handle"></a>task_handle

构造新的 `task_handle` 对象。 任务的工作是通过调用指定为构造函数的参数的函数来执行的。

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>参数

*_Func*<br/>
将调用以执行 `task_handle` 对象表示的工作的函数。 这可能是 lambda 函子、指向函数的指针，或支持具有签名 `void operator()()`的函数调用运算符版本的任何对象。

### <a name="remarks"></a>备注

运行时创建要传递给构造函数的工作函数的副本。 因此，传递到 `task_handle` 对象的函数对象中发生的任何状态更改都不会出现在该函数对象的副本中。

## <a name="dtor"></a>~ task_handle

销毁 `task_handle` 的对象。

```cpp
~task_handle();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[task_group 类](task-group-class.md)<br/>
[structured_task_group 类](structured-task-group-class.md)
