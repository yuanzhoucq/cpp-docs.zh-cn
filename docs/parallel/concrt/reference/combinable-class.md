---
title: combinable 类
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: d445b8ac1d2a8487e9e1ec4f21f63cf5ef071e91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224963"
---
# <a name="combinable-class"></a>combinable 类

`combinable<T>` 对象旨在提供数据的线程专用副本，以在并行算法期间执行无锁线程本地子计算。 在并行操作结束时，线程专用子计算可随之合并到最终结果。 此类可替代共享变量使用，并可能会带来性能提升（如果该共享变量上存在大量争用）。

## <a name="syntax"></a>语法

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>参数

*T*<br/>
最终合并结果的数据类型。 该类型必须具有一个复制构造函数和一个默认构造函数。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[combinable](#ctor)|已重载。 构造新的 `combinable` 对象。|
|[~ 合并析构函数](#dtor)|销毁 `combinable` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[清除](#clear)|清除以前使用的任何中间计算结果。|
|[or](#combine)|通过调用提供的组合函子，从线程本地子计算集中计算最终值。|
|[combine_each](#combine_each)|通过为每个线程本地子计算调用提供的组合函子，计算一组线程本地子计算的最终值。 最终的结果是由函数对象累积的。|
|[地方](#local)|已重载。 返回对线程专用子计算的引用。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[operator =](#operator_eq)|`combinable`从另一个对象分配给 `combinable` 对象。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`combinable`

## <a name="requirements"></a>要求

**标头：** ppl。h

**命名空间：** 并发

## <a name="clear"></a><a name="clear"></a>清除

清除以前使用的任何中间计算结果。

```cpp
void clear();
```

## <a name="combinable"></a><a name="ctor"></a>组合

构造新的 `combinable` 对象。

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>参数

*_Function*<br/>
初始化函子对象的类型。

*_FnInitialize*<br/>
一个函数，将调用该函数来初始化类型的每个新的线程私有值 `T` 。 它必须支持具有签名的函数调用运算符 `T ()` 。

*_Copy*<br/>
`combinable`要复制到此对象的现有对象。

### <a name="remarks"></a>备注

第一个构造函数用该类型的默认构造函数初始化新元素 `T` 。

第二个构造函数使用作为参数提供的初始化函子初始化新元素 `_FnInitialize` 。

第三个构造函数是复制构造函数。

## <a name="combinable"></a><a name="dtor"></a>~ 组合

销毁 `combinable` 对象。

```cpp
~combinable();
```

## <a name="combine"></a><a name="combine"></a>or

通过调用提供的组合函子，从线程本地子计算集中计算最终值。

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>参数

*_Function*<br/>
将调用以合并两个线程本地子计算的函数对象的类型。

*_FnCombine*<br/>
用于组合子计算的函子。 其签名为 `T (T, T)` 或 `T (const T&, const T&)` ，并且必须是关联的，并且可交换。

### <a name="return-value"></a>返回值

合并所有线程私有子计算的最终结果。

## <a name="combine_each"></a><a name="combine_each"></a>combine_each

通过为每个线程本地子计算调用提供的组合函子，计算一组线程本地子计算的最终值。 最终的结果是由函数对象累积的。

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>参数

*_Function*<br/>
将调用以合并单个线程本地子计算的函数对象的类型。

*_FnCombine*<br/>
用于合并一个子计算的函子。 其签名为 `void (T)` 或 `void (const T&)` ，并且必须是关联的和可交换的。

## <a name="local"></a><a name="local"></a>地方

返回对线程专用子计算的引用。

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>参数

*_Exists*<br/>
对布尔值的引用。 如果此线程中已存在子计算，则此参数引用的布尔值将设置为， **`true`** **`false`** 如果这是此线程上的第一个子计算，则设置为。

### <a name="return-value"></a>返回值

对线程私有子计算的引用。

## <a name="operator"></a><a name="operator_eq"></a>operator =

`combinable`从另一个对象分配给 `combinable` 对象。

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>参数

*_Copy*<br/>
`combinable`要复制到此对象的现有对象。

### <a name="return-value"></a>返回值

对此对象的引用 `combinable` 。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
