---
title: CComSingleThreadModel 类
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 3d8169c999ba96049bc711033f7ba2ef53989663
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327331"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel 类

此类提供递增和递减变量值的方法。

## <a name="syntax"></a>语法

```
class CComSingleThreadModel
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CCom 单线程模型：：自动临界部分](#autocriticalsection)|引用类[CComFake 临界节](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CCom 单线程模型：：关键部分](#criticalsection)|引用类`CComFakeCriticalSection`。|
|[CCom 单线程模型：：线程模型NoCS](#threadmodelnocs)|引用`CComSingleThreadModel`.|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom 单线程模型：:D](#decrement)|声明指定变量的值。 此实现不是线程安全的。|
|[CCom 单线程模型：增量](#increment)|增加指定变量的值。 此实现不是线程安全的。|

## <a name="remarks"></a>备注

`CComSingleThreadModel`提供了递增和递减变量值的方法。 与[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)不同，这些方法不是线程安全的。

通常，您可以通过两`CComSingleThreadModel`个**类型定义**名称之一[（CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel）使用](atl-typedefs.md#ccomglobalsthreadmodel)。 每个**typedef**引用的类取决于所使用的线程模型，如下表所示：

|typedef|单线程模型|公寓线程模型|免费线程模型|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`;M#`CComMultiThreadModel`

`CComSingleThreadModel`本身定义三**个类型定义**名称。 `ThreadModelNoCS`引用`CComSingleThreadModel`. `AutoCriticalSection`和`CriticalSection`引用类[CComFake临界节](../../atl/reference/ccomfakecriticalsection-class.md)，它提供了与获取和释放关键部分的所有权相关的空方法。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CCom 单线程模型：：自动临界部分

使用`CComSingleThreadModel`时 **，typedef** `AutoCriticalSection`名称引用类[CComFake临界节](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>备注

因为`CComFakeCriticalSection`不提供关键部分，因此其方法不执行任何操作。

[CCom 多线程模型](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含`AutoCriticalSection`的定义。 下表显示了线程模型类与 引用`AutoCriticalSection`的关键节类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除 之外`AutoCriticalSection`，还可以使用**typedef**名称["临界节](#criticalsection)"。 如果要消除 CRT 启动代码，不应在全局对象或静态类成员中指定`AutoCriticalSection`。

### <a name="example"></a>示例

请参阅[CCom 多线程模型：：自动临界节](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CCom 单线程模型：：关键部分

使用`CComSingleThreadModel`时 **，typedef** `CriticalSection`名称引用类[CComFake临界节](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>备注

因为`CComFakeCriticalSection`不提供关键部分，因此其方法不执行任何操作。

[CCom 多线程模型](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含`CriticalSection`的定义。 下表显示了线程模型类与 引用`CriticalSection`的关键节类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除 之外`CriticalSection`，还可以使用**typedef**名称[Auto临界节](#autocriticalsection)。 如果要消除 CRT 启动代码，不应在全局对象或静态类成员中指定`AutoCriticalSection`。

### <a name="example"></a>示例

请参阅[CCom 多线程模型：：自动临界节](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CCom 单线程模型：:D

此静态函数会递减*p*指向的变量的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向要递减的变量的指针。

### <a name="return-value"></a>返回值

递减的结果。

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CCom 单线程模型：增量

此静态函数递增*p*指向的变量的值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向要递增的变量的指针。

### <a name="return-value"></a>返回值

增量的结果。

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CCom 单线程模型：：线程模型NoCS

使用`CComSingleThreadModel`时 **，typedef** `ThreadModelNoCS`名称仅`CComSingleThreadModel`引用 。

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>备注

[CCom 多线程模型](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含`ThreadModelNoCS`的定义。 下表显示了线程模型类与 引用的`ThreadModelNoCS`类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>示例

请参阅[CCom 多线程模型：：自动临界节](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
