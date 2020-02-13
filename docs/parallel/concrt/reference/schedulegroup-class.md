---
title: ScheduleGroup 类
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: 8686b5ef0906e3188a1e683d1190bbe6124cd19e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143272"
---
# <a name="schedulegroup-class"></a>ScheduleGroup 类

表示计划组的抽象。 计划组整理受益于在时间上（通过在移动到另一个组之前执行同一个组中的另一个任务）或空间上（通过在同一 NUMA 节点或物理套接字上执行同一个组内的多个项）紧密计划在一起的一组相关工作。

## <a name="syntax"></a>语法

```cpp
class ScheduleGroup;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>受保护构造函数

|名称|说明|
|----------|-----------------|
|[~ ScheduleGroup 析构函数](#dtor)||

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Id](#id)|返回计划组的标识符，该标识符在该组所属的计划程序中是唯一的。|
|[参考](#reference)|递增计划组的引用计数。|
|[发布](#release)|递减计划程序组的引用计数。|
|[ScheduleTask](#scheduletask)|计划计划组内的轻量任务。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`ScheduleGroup`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="id"></a>识别

返回计划组的标识符，该标识符在该组所属的计划程序中是唯一的。

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>返回值

计划组的标识符，该标识符在该组所属的计划程序中是唯一的。

## <a name="operator_delete"></a>运算符删除

当释放对象的所有外部引用时，运行时在内部销毁 `ScheduleGroup` 的对象。 不能显式删除它。

```cpp
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
const char *,
    int);
```

### <a name="parameters"></a>参数

*_PObject*<br/>
指向要删除的对象的指针。

## <a name="reference"></a>对

递增计划组的引用计数。

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>返回值

新增加的引用计数。

### <a name="remarks"></a>备注

这通常用于管理组合的计划组的生存期。 当计划组的引用计数降为零时，计划组会被运行时删除。 使用[CurrentScheduler：： CreateScheduleGroup](currentscheduler-class.md#createschedulegroup)方法创建的计划组，或[计划程序：： CreateScheduleGroup](scheduler-class.md#createschedulegroup)方法开始时引用计数为1。

## <a name="release"></a>拆卸

递减计划程序组的引用计数。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>返回值

新递减的引用计数。

### <a name="remarks"></a>备注

这通常用于管理组合的计划组的生存期。 当计划组的引用计数降为零时，计划组会被运行时删除。 调用 `Release` 方法特定次数来移除创建引用数和使用 `Reference` 方法放置的任何其他引用后，您将无法进一步使用计划组。 这样做将导致未定义的行为。

计划组与特定计划程序实例相关联。 必须确保对于计划组的所有引用都在所有对计划程序的引用释放之前释放，因为后者可能导致计划程序破坏。 否则，会导致未定义的行为。

## <a name="dtor"></a>~ ScheduleGroup

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a>ScheduleTask

计划计划组内的轻量任务。

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>参数

*_Proc*<br/>
一个指针，指向用于执行轻量任务的主体的函数。

*_Data*<br/>
指向将作为参数传递给任务正文的数据的 void 指针。

### <a name="remarks"></a>备注

调用 `ScheduleTask` 方法会将引用计数隐式放置在任务执行后在适当时间由运行时删除的计划组。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[CurrentScheduler 类](currentscheduler-class.md)<br/>
[Scheduler 类](scheduler-class.md)<br/>
[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
