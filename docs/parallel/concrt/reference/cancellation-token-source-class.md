---
title: cancellation_token_source 类
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
ms.openlocfilehash: 131c4155ad902221d14f90f750f89c31479e2067
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142232"
---
# <a name="cancellation_token_source-class"></a>cancellation_token_source 类

`cancellation_token_source` 类表示取消某个可取消操作的功能。

## <a name="syntax"></a>语法

```cpp
class cancellation_token_source;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[cancellation_token_source](#ctor)|已重载。 构造一个新的 `cancellation_token_source`。 该源可用于标记某个可取消操作的取消。|
|[~ cancellation_token_source 析构函数](#dtor)||

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[cancel](#cancel)|取消标记。 所有使用标记的 `task_group`、`structured_task_group` 或 `task` 将在进行此调用时取消，并将在下一个中断点引发异常。|
|[create_linked_source](#create_linked_source)|已重载。 创建一个 `cancellation_token_source`，并在取消提供的标记时将其取消。|
|[get_token](#get_token)|返回一个与此源相关联的取消标记。 如果发生取消操作，则可能轮询返回的标记以进行取消或提供回调。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`cancellation_token_source`

## <a name="requirements"></a>要求

**标头：** pplcancellation_token。h

**命名空间：** 并发

## <a name="dtor"></a>~ cancellation_token_source

```cpp
~cancellation_token_source();
```

## <a name="cancel"></a>取消

取消标记。 所有使用标记的 `task_group`、`structured_task_group` 或 `task` 将在进行此调用时取消，并将在下一个中断点引发异常。

```cpp
void cancel() const;
```

## <a name="ctor"></a>cancellation_token_source

构造一个新的 `cancellation_token_source`。 该源可用于标记某个可取消操作的取消。

```cpp
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```

### <a name="parameters"></a>参数

*_Src*<br/>
要复制或移动的对象。

## <a name="create_linked_source"></a>create_linked_source

创建一个 `cancellation_token_source`，并在取消提供的标记时将其取消。

```cpp
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```

### <a name="parameters"></a>参数

*_Iter*<br/>
迭代器类型。

*_Src*<br/>
一个标记，如果取消该标记，则将导致取消返回的标记源。 请注意，返回的标记源也可在此参数中包含的源之外单独取消。

*_Begin*<br/>
与C++用于侦听取消的标记范围的开头相对应的标准库迭代器。

*_End*<br/>
与C++用于侦听取消的标记范围相对应的标准库迭代器。

### <a name="return-value"></a>返回值

在取消 `cancellation_token_source` 参数提供的标记时取消的 `_Src`。

## <a name="get_token"></a>get_token

返回一个与此源相关联的取消标记。 如果发生取消操作，则可能轮询返回的标记以进行取消或提供回调。

```cpp
cancellation_token get_token() const;
```

### <a name="return-value"></a>返回值

与此源关联的取消标记。

## <a name="operator_neq"></a>operator！ =

```cpp
bool operator!= (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>参数

*_Src*<br/>
操作数.

### <a name="return-value"></a>返回值

## <a name="operator_eq"></a>operator =

```cpp
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```

### <a name="parameters"></a>参数

*_Src*<br/>
操作数.

### <a name="return-value"></a>返回值

## <a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>参数

*_Src*<br/>
操作数.

### <a name="return-value"></a>返回值

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
