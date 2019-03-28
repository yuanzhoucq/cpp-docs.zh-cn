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
ms.openlocfilehash: 4075051ec07fc1331d815534a715c0411160fe14
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58566021"
---
# <a name="acceleratorview-class"></a>accelerator_view 类

表示 c + + AMP 数据并行快捷键上的虚拟设备抽象。

### <a name="syntax"></a>语法

```
class accelerator_view;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[accelerator_view 构造函数](#ctor)|初始化 `accelerator_view` 类的新实例。|
|[~ accelerator_view 析构函数](#dtor)|销毁`accelerator_view`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[create_marker](#create_marker)|返回将来以跟踪到此提交到目前为止的所有命令的完成`accelerator_view`对象。|
|[flush](#flush)|提交所有挂起命令排队到`accelerator_view`给快捷键用于执行对象。|
|[get_accelerator](#get_accelerator)|返回 `accelerator` 对象的 `accelerator_view` 对象。|
|[get_is_auto_selection](#get_is_auto_selection)|返回一个布尔值，该值指示是否在运行时将自动选择适当的快捷键时`accelerator_view`对象传递给[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。|
|[get_is_debug](#get_is_debug)|返回一个布尔值，该值指示是否`accelerator_view`对象具有为广泛错误报告启用了调试层。|
|[get_queuing_mode](#get_queuing_mode)|返回的排队模式`accelerator_view`对象。|
|[get_version](#get_version)|返回的版本`accelerator_view`。|
|[wait](#wait)|等待所有命令提交到`accelerator_view`对象才能完成。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator!=](#operator_neq)|比较此`accelerator_view`与另一个对象，并返回**false**如果它们是相同的; 否则返回**true**。|
|[operator=](#operator_eq)|将指定的内容复制`accelerator_view`到此对象。|
|[operator==](#operator_eq_eq)|比较此`accelerator_view`与另一个对象，并返回**true**如果它们是相同的; 否则返回**false**。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[accelerator](#accelerator)|获取 `accelerator_view` 对象的 `accelerator` 对象。|
|[is_auto_selection](#is_auto_selection)|获取一个布尔值，该值指示是否在运行时将自动选择适当的快捷键时`accelerator_view`对象传递给[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。|
|[is_debug](#is_debug)|获取一个布尔值，该值指示是否`accelerator_view`对象具有为广泛错误报告启用了调试层。|
|[queuing_mode](#queuing_mode)|获取的排队模式`accelerator_view`对象。|
|[版本](#version)|获取加速器的版本。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`accelerator_view`

### <a name="remarks"></a>备注

`accelerator_view`对象表示加速器的逻辑的、 独立视图。 单个物理计算设备可以有许多逻辑的、 独立`accelerator_view`对象。 每个加速器都有默认值`accelerator_view`对象。 其他`accelerator_view`可创建对象。

可以在多个客户端线程之间共享的物理设备。 客户端线程可以以协作方式使用相同`accelerator_view`对象的快捷键或每个客户端可以与通过独立计算设备通信`accelerator_view`其他客户端线程相隔离的对象。

`accelerator_view`对象都可以有一个两个[queuing_mode 枚举](concurrency-namespace-enums-amp.md#queuing_mode)状态。 如果排队模式为`immediate`，命令，如`copy`和`parallel_for_each`只要它们返回给调用方发送到相应的加速器设备。 如果排队模式为`deferred`，此类命令在对应的命令队列排队等候`accelerator_view`对象。 命令不会实际发送到设备之前`flush()`调用。

## <a name="requirements"></a>要求

**标头：** amprt.h

**命名空间：** 并发

## <a name="accelerator"></a> 快捷键

获取 accelerator_view 对象快捷键对象。

### <a name="syntax"></a>语法

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a> accelerator_view

Accelerator_view 类的新实例初始化通过复制现有`accelerator_view`对象。

### <a name="syntax"></a>语法

```
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>参数

*other*<br/>
`accelerator_view`要复制对象。

## <a name="createmarker"></a>create_marker

返回将来以跟踪到此提交到目前为止的所有命令的完成`accelerator_view`对象。

### <a name="syntax"></a>语法

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>返回值

将来以跟踪到此提交到目前为止的所有命令的完成`accelerator_view`对象。

## <a name="flush"></a>flush

提交所有挂起的命令排队到给快捷键用于执行的 accelerator_view 对象。

### <a name="syntax"></a>语法

```
void flush();
```

### <a name="return-value"></a>返回值

返回 `void`。

## <a name="getaccelerator"></a>get_accelerator

返回视图对象的快捷键对象。
### <a name="syntax"></a>语法

```
accelerator get_accelerator() const;
```

### <a name="return-value"></a>返回值

Accelerator_view 对象的快捷键对象。

## <a name="getisautoselection"></a>get_is_auto_selection

返回一个布尔值，该值指示当 accelerator_view 传递给是否在运行时将自动选择适当的快捷键[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。

### <a name="syntax"></a>语法

```
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>返回值

**true**如果在运行时将自动选择适当的快捷键; 否则为**false**。

## <a name="getisdebug"></a>get_is_debug

返回一个布尔值，该值指示视图对象是否具有为广泛错误报告启用了调试层。

### <a name="syntax"></a>语法

```
bool get_is_debug() const;
```

### <a name="return-value"></a>返回值

一个布尔值，指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。

## <a name="getqueuingmode"></a>get_queuing_mode

返回视图对象的排队模式。

### <a name="syntax"></a>语法

```
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>返回值

`accelerator_view` 对象的排队模式。

## <a name="getversion"></a>get_version

返回 accelerator_view 的版本。

### <a name="syntax"></a>语法

```
unsigned int get_version() const;
```

### <a name="return-value"></a>返回值

版本的`accelerator_view`。

## <a name="isautoselection"></a>is_auto_selection

获取一个布尔值，该值指示当 accelerator_view 传递给是否在运行时将自动选择适当的快捷键[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。

### <a name="syntax"></a>语法

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="isdebug"></a>is_debug

获取一个布尔值，该值指示视图对象是否具有为广泛错误报告启用了调试层。

### <a name="syntax"></a>语法

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator_neq"></a> 运算符 ！ =

比较此 accelerator_view 对象与另一个，并返回**false**如果它们是相同的; 否则，返回**true**。

### <a name="syntax"></a>语法

```
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>参数

*other*<br/>
与此对象相比较的 `accelerator_view` 对象。

### <a name="return-value"></a>返回值

**false**如果两个对象都相同; 否则为**true**。

## <a name="operator_eq"></a> 运算符 =

将指定的 accelerator_view 对象的内容复制到此。

### <a name="syntax"></a>语法

```
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>参数

*other*<br/>
`accelerator_view`要从复制对象。

### <a name="return-value"></a>返回值

对修改后的 `accelerator_view` 对象的引用。

## <a name="operator_eq_eq"></a> 运算符 = =

比较此 accelerator_view 对象与另一个，并返回 **，则返回 true**如果它们是相同的; 否则，返回**false**。

### <a name="syntax"></a>语法

```
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>参数

*other*<br/>
与此对象相比较的 `accelerator_view` 对象。

### <a name="return-value"></a>返回值

**true**如果两个对象都相同; 否则为**false**。

## <a name="queuingmode"></a>queuing_mode

获取 accelerator_view 对象排队模式。

### <a name="syntax"></a>语法

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

获取 accelerator_view 的版本。

### <a name="syntax"></a>语法

```
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>等待

等待所有命令提交到 accelerator_view 对象才能完成。

### <a name="syntax"></a>语法

```
void wait();
```

### <a name="return-value"></a>返回值

返回 `void`。

### <a name="remarks"></a>备注

如果[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)是`immediate`，此方法将立即返回而不会阻塞。

##  <a name="dtor"></a> ~accelerator_view

销毁视图对象。

### <a name="syntax"></a>语法

```
~accelerator_view();
```

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
