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
ms.openlocfilehash: 05256516c0a693a282b8d0de56d6c9e7465f2740
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299967"
---
# <a name="combinable-class"></a>combinable 类


  `combinable<T>` 对象旨在提供数据的线程专用副本，以在并行算法期间执行无锁线程本地子计算。 在并行操作结束时，线程专用子计算可随之合并到最终结果。 此类可替代共享变量使用，并可能会带来性能提升（如果该共享变量上存在大量争用）。

## <a name="syntax"></a>语法

```
template<typename T>
class combinable;
```

#### <a name="parameters"></a>参数

*T*<br/>
最终的合并结果数据类型。 类型必须具有一个复制构造函数和默认构造函数。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[combinable](#ctor)|已重载。 构造一个新`combinable`对象。|
|[~ combinable 析构函数](#dtor)|销毁 `combinable` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[clear](#clear)|清除任何以前的使用情况的中间计算结果。|
|[combine](#combine)|通过调用提供的 combine 函子计算的线程本地子计算集的最终值。|
|[combine_each](#combine_each)|通过调用每个线程本地子计算一次提供的合并函子计算的线程本地子计算集的最终值。 最终结果被累积的函数对象。|
|[local](#local)|已重载。 返回到线程专用子计算的引用。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator=](#operator_eq)|将分配给`combinable`从另一个对象`combinable`对象。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`combinable`

## <a name="requirements"></a>要求

**标头：** ppl.h

**命名空间：** 并发

##  <a name="clear"></a> 清除

清除任何以前的使用情况的中间计算结果。

```
void clear();
```

##  <a name="ctor"></a> combinable

构造一个新`combinable`对象。

```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>参数

*_Function*<br/>
初始化函子对象的类型。

*_FnInitialize*<br/>
一个函数，它将调用以初始化的类型的每个新线程专用值`T`。 它必须支持具有签名的函数调用运算符`T ()`。

*_Copy*<br/>
将现有`combinable`要复制到此对象。

### <a name="remarks"></a>备注

第一个构造函数初始化新元素类型的默认构造函数`T`。

使用提供的初始化函子的新元素的第二个构造函数初始化`_FnInitialize`参数。

第三个构造函数是复制构造函数。

##  <a name="dtor"></a> ~combinable

销毁 `combinable` 对象。

```
~combinable();
```

##  <a name="combine"></a> combine

通过调用提供的 combine 函子计算的线程本地子计算集的最终值。

```
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>参数

*_Function*<br/>
要调用以组合两个线程本地子计算的函数对象的类型。

*_FnCombine*<br/>
用于组合子计算仿函数。 其签名就`T (T, T)`或`T (const T&, const T&)`，并且它必须是关联性和可交换性。

### <a name="return-value"></a>返回值

合并所有线程专用子计算最终结果。

##  <a name="combine_each"></a> combine_each

通过调用每个线程本地子计算一次提供的合并函子计算的线程本地子计算集的最终值。 最终结果被累积的函数对象。

```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>参数

*_Function*<br/>
将调用要合并单个的线程本地子计算的函数对象的类型。

*_FnCombine*<br/>
用于将某一子计算仿函数。 其签名就`void (T)`或`void (const T&)`，并且必须是关联性和可交换性。

##  <a name="local"></a> local

返回到线程专用子计算的引用。

```
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>参数

*_Exists*<br/>
一个布尔值对的引用。 此参数由引用的布尔值将设置为 **，则返回 true**如果子计算已存在，此线程上并设置为**false**如果这是此线程上的第一个子计算。

### <a name="return-value"></a>返回值

对线程专用子计算的引用。

##  <a name="operator_eq"></a> 运算符 =

将分配给`combinable`从另一个对象`combinable`对象。

```
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>参数

*_Copy*<br/>
将现有`combinable`要复制到此对象。

### <a name="return-value"></a>返回值

对此引用`combinable`对象。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
