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
ms.openlocfilehash: f3be8cc3ab9a0f36027cc38c88f026570d1fdb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370892"
---
# <a name="accelerator_view-class"></a>accelerator_view 类

表示 C++ AMP 数据并行加速器上的虚拟设备抽象。

## <a name="syntax"></a>语法

```cpp
class accelerator_view;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[accelerator_view构造函数](#ctor)|初始化 `accelerator_view` 类的新实例。|
|[*accelerator_view析构图](#dtor)|销毁`accelerator_view`对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[create_marker](#create_marker)|返回一个未来，以跟踪到目前为止提交给此`accelerator_view`对象的所有命令的完成情况。|
|[冲洗](#flush)|将所有排队到对象等待`accelerator_view`执行的挂起命令提交到加速器执行。|
|[get_accelerator](#get_accelerator)|返回 `accelerator` 对象的 `accelerator_view` 对象。|
|[get_is_auto_selection](#get_is_auto_selection)|返回一个布尔值，指示当`accelerator_view`对象传递给[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)时，运行时是否将自动选择适当的快捷键。|
|[get_is_debug](#get_is_debug)|返回一个布尔值，指示`accelerator_view`对象是否启用了 DEBUG 层以进行大量错误报告。|
|[get_queuing_mode](#get_queuing_mode)|返回`accelerator_view`对象的排队模式。|
|[get_version](#get_version)|返回 的版本`accelerator_view`。|
|[等](#wait)|等待提交到`accelerator_view`对象的所有命令完成。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[操作员！](#operator_neq)|将此`accelerator_view`对象与另一个对象进行比较，如果对象相同，则返回**false;** 否则，返回**true**。|
|[运算符*](#operator_eq)|将指定`accelerator_view`对象的内容复制到此对象中。|
|[运算符*](#operator_eq_eq)|将此`accelerator_view`对象与另一个对象进行比较，如果对象相同，则返回**true;** 否则，返回**false**。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[加速器](#accelerator)|获取 `accelerator_view` 对象的 `accelerator` 对象。|
|[is_auto_selection](#is_auto_selection)|获取布尔值，指示当`accelerator_view`对象传递到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)时，运行时是否将自动选择适当的加速器。|
|[is_debug](#is_debug)|获取布尔值，指示`accelerator_view`对象是否已启用 DEBUG 层以进行大量错误报告。|
|[queuing_mode](#queuing_mode)|获取`accelerator_view`对象的排队模式。|
|[version](#version)|获取快捷键的版本。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`accelerator_view`

### <a name="remarks"></a>备注

对象`accelerator_view`表示加速器的逻辑隔离视图。 单个物理计算设备可以具有许多逻辑隔离`accelerator_view`对象。 每个加速器都有一个`accelerator_view`默认对象。 可以`accelerator_view`创建其他对象。

物理设备可以在许多客户端线程之间共享。 客户端线程可以协同使用加速器的同一`accelerator_view`对象，或者每个客户端可以通过独立`accelerator_view`对象与计算设备通信，以便与其他客户端线程隔离。

对象`accelerator_view`可以具有两[个queuing_mode枚举](concurrency-namespace-enums-amp.md#queuing_mode)状态之一。 如果队列模式为`immediate`，则命令`copy`，`parallel_for_each`如 和 的命令在返回调用方后立即发送到相应的加速器设备。 如果排队模式为`deferred`，则此类命令在对应于`accelerator_view`对象的命令队列上排队。 在调用命令之前`flush()`，实际上不会将命令发送到设备。

## <a name="requirements"></a>要求

**标题：** amprt.h

**命名空间：** 并发

## <a name="accelerator"></a><a name="accelerator"></a>加速器

获取accelerator_view对象的快捷键对象。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a>accelerator_view

通过复制现有`accelerator_view`对象来初始化accelerator_view类的新实例。

### <a name="syntax"></a>语法

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>参数

*其他*<br/>
要复制的 `accelerator_view` 对象。

## <a name="create_marker"></a><a name="create_marker"></a>create_marker

返回一个未来，以跟踪到目前为止提交给此`accelerator_view`对象的所有命令的完成情况。

### <a name="syntax"></a>语法

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>返回值

跟踪到目前为止提交给此`accelerator_view`对象的所有命令的完成情况。

## <a name="flush"></a>flush

将针对 accelerator_view 对象排队的所有挂起命令提交给快捷键执行。

### <a name="syntax"></a>语法

```cpp
void flush();
```

### <a name="return-value"></a>返回值

返回 `void`。

## <a name="get_accelerator"></a><a name="get_accelerator"></a>get_accelerator

返回accelerator_view对象的快捷键对象。

### <a name="syntax"></a>语法

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>返回值

accelerator_view对象的快捷键对象。

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection

返回一个布尔值，指示当accelerator_view传递到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)时，运行时是否将自动选择适当的加速器。

### <a name="syntax"></a>语法

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>返回值

如果运行时将自动选择适当的加速器，**则为 true;** 否则，**假**。

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

返回一个布尔值，指示 accelerator_view 对象是否为广泛的错误报告启用了调试层。

### <a name="syntax"></a>语法

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>返回值

一个布尔值，指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a>get_queuing_mode

返回 accelerator_view 对象排队模式。

### <a name="syntax"></a>语法

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>返回值

`accelerator_view` 对象的排队模式。

## <a name="get_version"></a><a name="get_version"></a>get_version

返回 accelerator_view 的版本。

### <a name="syntax"></a>语法

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>返回值

`accelerator_view` 的版本。

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a>is_auto_selection

获取布尔值，指示当accelerator_view传递到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)时，运行时是否将自动选择适当的加速器。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

获取一个布尔值，指示 accelerator_view 对象是否为广泛的错误报告启用了调试层。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a>操作员！

将此accelerator_view对象与另一个对象进行比较，如果对象相同，则返回**false;** 否则，返回**true**。

### <a name="syntax"></a>语法

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
与此对象相比较的 `accelerator_view` 对象。

### <a name="return-value"></a>返回值

如果两个对象相同，**则为 false;** 否则，**真**。

## <a name="operator"></a><a name="operator_eq"></a>运算符*

将指定accelerator_view对象的内容复制到此对象中。

### <a name="syntax"></a>语法

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>参数

*其他*<br/>
要`accelerator_view`复制的对象。

### <a name="return-value"></a>返回值

对修改后的 `accelerator_view` 对象的引用。

## <a name="operator"></a><a name="operator_eq_eq"></a>运算符*

将此accelerator_view对象与另一个对象进行比较，如果对象相同，则返回**true;** 否则，返回**false**。

### <a name="syntax"></a>语法

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>参数

*其他*<br/>
与此对象相比较的 `accelerator_view` 对象。

### <a name="return-value"></a>返回值

如果两个对象相同，**则为 true;** 否则，**假**。

## <a name="queuing_mode"></a><a name="queuing_mode"></a>queuing_mode

获取accelerator_view对象的排队模式。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>版本

获取 accelerator_view 的版本。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

等待提交到对象accelerator_view的所有命令完成。

### <a name="syntax"></a>语法

```cpp
void wait();
```

### <a name="return-value"></a>返回值

返回 `void`。

### <a name="remarks"></a>备注

如果[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)为`immediate`，则此方法将立即返回而不阻塞。

## <a name="accelerator_view"></a><a name="dtor"></a>*accelerator_view

销毁accelerator_view对象。

### <a name="syntax"></a>语法

```cpp
~accelerator_view();
```

## <a name="see-also"></a>另请参阅

[Concurrency 命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
