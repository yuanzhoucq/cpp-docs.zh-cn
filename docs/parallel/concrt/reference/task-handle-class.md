---
title: task_handle 类
ms.date: 11/04/2016
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: c1a12555b0b7277fd6b52d935518e4bb1f297285
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521354"
---
# <a name="taskhandle-class"></a>task_handle 类

`task_handle` 类表示单个并行工作项。 它封装执行一项工作所需的指令和数据。

## <a name="syntax"></a>语法

```
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

#### <a name="parameters"></a>参数

*_Function*<br/>
将调用来执行工作所表示的函数对象的类型`task_handle`对象。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[task_handle](#ctor)|构造一个新`task_handle`对象。 通过调用作为构造函数的参数指定的函数执行该任务的工作。|
|[~ task_handle 析构函数](#dtor)|销毁`task_handle`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|运行时将调用来执行任务句柄的工作函数调用运算符。|

## <a name="remarks"></a>备注

`task_handle` 可以结合使用的对象`structured_task_group`或更多常规`task_group`对象，若要将工作分解为并行任务。 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

请注意，创建者`task_handle`对象是负责维护创建的生存期`task_handle`对象，直到并发运行时不再需要它。 通常情况下，这意味着`task_handle`对象必须销毁，直到`wait`或`run_and_wait`方法`task_group`或`structured_task_group`已调用到其排队。

`task_handle` 对象通常是与 c + + lambda 结合使用。 因为您不知道 lambda 的真实类型[make_task](concurrency-namespace-functions.md#make_task)函数通常用于创建`task_handle`对象。

运行时创建一份工作函数传递给`task_handle`对象。 因此，在函数中发生的任何状态更改对象传递给`task_handle`对象不会显示在该函数对象的副本。

## <a name="inheritance-hierarchy"></a>继承层次结构

`task_handle`

## <a name="requirements"></a>要求

**标头：** ppl.h

**命名空间：** 并发

##  <a name="task_handle__operator_call"></a> operator （)

运行时将调用来执行任务句柄的工作函数调用运算符。

```
void operator()() const;

```

##  <a name="task_handle__ctor"></a> task_handle

构造一个新`task_handle`对象。 通过调用作为构造函数的参数指定的函数执行该任务的工作。

```
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>参数

*_Func*<br/>
将调用来执行工作所表示的函数`task_handle`对象。 这可能是 lambda 函数，指向函数，也支持具有签名的函数调用运算符的版本的任何对象`void operator()()`。

### <a name="remarks"></a>备注

运行时创建一份工作函数传递给构造函数。 因此，在函数中发生的任何状态更改对象传递给`task_handle`对象不会显示在该函数对象的副本。

##  <a name="dtor"></a> ~ task_handle

销毁`task_handle`对象。

```
~task_handle();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[task_group 类](task-group-class.md)<br/>
[structured_task_group 类](structured-task-group-class.md)
