---
title: accelerator_view 类
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 8990566fb3a700d61de324f725dea3ec00006d04
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127171"
---
# <a name="accelerator_view-class"></a>accelerator_view 类

表示C++ AMP 数据并行加速器上的虚拟设备抽象。

## <a name="syntax"></a>语法

```cpp
class accelerator_view;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[accelerator_view 构造函数](#ctor)|初始化 `accelerator_view` 类的新实例。|
|[~ accelerator_view 析构函数](#dtor)|销毁 `accelerator_view` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[create_marker](#create_marker)|返回一个将来跟踪迄今为止向此 `accelerator_view` 对象提交的所有命令的完成。|
|[flush](#flush)|将排队到 `accelerator_view` 对象的所有挂起命令提交给快捷键以便执行。|
|[get_accelerator](#get_accelerator)|返回 `accelerator` 对象的 `accelerator_view` 对象。|
|[get_is_auto_selection](#get_is_auto_selection)|返回一个布尔值，该值指示在 `accelerator_view` 对象传递到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)时，运行时是否将自动选择适当的快捷键。|
|[get_is_debug](#get_is_debug)|返回一个布尔值，该值指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。|
|[get_queuing_mode](#get_queuing_mode)|返回 `accelerator_view` 对象的排队模式。|
|[get_version](#get_version)|返回 `accelerator_view`的版本。|
|[再](#wait)|等待提交到 `accelerator_view` 对象的所有命令完成。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator!=](#operator_neq)|将此 `accelerator_view` 对象与另一个对象进行比较，如果二者相同，则返回**false** ;否则，返回**true**。|
|[operator=](#operator_eq)|将指定 `accelerator_view` 对象的内容复制到此对象中。|
|[operator==](#operator_eq_eq)|将此 `accelerator_view` 对象与另一个对象进行比较，如果相等，则返回**true** ;否则，返回**false**。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[键](#accelerator)|获取 `accelerator` 对象的 `accelerator_view` 对象。|
|[is_auto_selection](#is_auto_selection)|获取一个布尔值，该值指示在 `accelerator_view` 对象传递到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)时，运行时是否将自动选择适当的快捷键。|
|[is_debug](#is_debug)|获取一个布尔值，该值指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。|
|[queuing_mode](#queuing_mode)|获取 `accelerator_view` 对象的排队模式。|
|[version](#version)|获取快捷键的版本。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`accelerator_view`

### <a name="remarks"></a>备注

`accelerator_view` 对象表示加速器的逻辑隔离视图。 单个物理计算设备可以有多个逻辑隔离的 `accelerator_view` 对象。 每个快捷键都有一个默认的 `accelerator_view` 对象。 可以创建其他 `accelerator_view` 对象。

物理设备可以在许多客户端线程之间共享。 客户端线程可以通过协作方式使用同一加速器 `accelerator_view` 对象，或每个客户端都可以通过独立的 `accelerator_view` 对象与计算设备通信，以便与其他客户端线程隔离。

`accelerator_view` 对象可以具有两个[Queuing_mode 枚举](concurrency-namespace-enums-amp.md#queuing_mode)状态之一。 如果 `immediate`队列模式，则在将 `copy` 和 `parallel_for_each` 等命令返回到调用方后，就会将其发送到相应的加速器设备。 如果 `deferred`队列模式，则此类命令将在与 `accelerator_view` 对象对应的命令队列中排队。 在调用 `flush()` 之前，不会实际将命令发送到设备。

## <a name="requirements"></a>要求

**标头：** amprt

**命名空间：** 并发

## <a name="accelerator"></a>键

获取 accelerator_view 对象的快捷键对象。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a>accelerator_view

通过复制现有的 `accelerator_view` 对象，初始化 accelerator_view 类的新实例。

### <a name="syntax"></a>语法

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>参数

*other*<br/>
要复制的 `accelerator_view` 对象。

## <a name="create_marker"></a>create_marker

返回一个将来跟踪迄今为止向此 `accelerator_view` 对象提交的所有命令的完成。

### <a name="syntax"></a>语法

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>返回值

将来跟踪迄今为止向此 `accelerator_view` 对象提交的所有命令是否完成。

## <a name="flush"></a>flush

将针对 accelerator_view 对象排队的所有挂起命令提交给快捷键执行。

### <a name="syntax"></a>语法

```cpp
void flush();
```

### <a name="return-value"></a>返回值

返回 `void`。

## <a name="get_accelerator"></a>get_accelerator

返回 accelerator_view 对象的快捷键对象。

### <a name="syntax"></a>语法

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>返回值

Accelerator_view 对象的快捷键对象。

## <a name="get_is_auto_selection"></a>get_is_auto_selection

返回一个布尔值，该值指示当 accelerator_view 传递到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)时，运行时是否将自动选择适当的快捷键。

### <a name="syntax"></a>语法

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>返回值

如果运行时将自动选择适当的快捷键，**则为 true** ;否则**为 false**。

## <a name="get_is_debug"></a>get_is_debug

返回一个布尔值，指示 accelerator_view 对象是否为广泛的错误报告启用了调试层。

### <a name="syntax"></a>语法

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>返回值

一个布尔值，指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。

## <a name="get_queuing_mode"></a>get_queuing_mode

返回 accelerator_view 对象排队模式。

### <a name="syntax"></a>语法

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>返回值

`accelerator_view` 对象的排队模式。

## <a name="get_version"></a>get_version

返回 accelerator_view 的版本。

### <a name="syntax"></a>语法

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>返回值

`accelerator_view` 的版本。

## <a name="is_auto_selection"></a>is_auto_selection

获取一个布尔值，该值指示当 accelerator_view 传递到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)时，运行时是否将自动选择适当的快捷键。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a>is_debug

获取一个布尔值，指示 accelerator_view 对象是否为广泛的错误报告启用了调试层。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator_neq"></a>operator！ =

将此 accelerator_view 对象与另一个对象进行比较，如果二者相同，则返回**false** ;否则，返回**true**。

### <a name="syntax"></a>语法

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>参数

*other*<br/>
与此对象相比较的 `accelerator_view` 对象。

### <a name="return-value"></a>返回值

如果两个对象相同，则为 false; 否则为**false** 。否则**为 true**。

## <a name="operator_eq"></a>operator =

将指定 accelerator_view 对象的内容复制到此对象中。

### <a name="syntax"></a>语法

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>参数

*other*<br/>
要从中进行复制的 `accelerator_view` 对象。

### <a name="return-value"></a>返回值

对修改后的 `accelerator_view` 对象的引用。

## <a name="operator_eq_eq"></a>operator = =

将此 accelerator_view 对象与另一个对象进行比较，如果相等，则返回**true** ;否则，返回**false**。

### <a name="syntax"></a>语法

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>参数

*other*<br/>
与此对象相比较的 `accelerator_view` 对象。

### <a name="return-value"></a>返回值

如果两个对象相同，则为**true** ;否则**为 false**。

## <a name="queuing_mode"></a>queuing_mode

获取 accelerator_view 对象的排队模式。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

获取 accelerator_view 的版本。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

等待提交到 accelerator_view 对象的所有命令完成。

### <a name="syntax"></a>语法

```cpp
void wait();
```

### <a name="return-value"></a>返回值

返回 `void`。

### <a name="remarks"></a>备注

如果 `immediate`[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) ，则此方法将立即返回，而不会阻止。

## <a name="dtor"></a>~ accelerator_view

销毁 accelerator_view 的对象。

### <a name="syntax"></a>语法

```cpp
~accelerator_view();
```

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
