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
ms.openlocfilehash: 05ef787764045ec7e17f5cdfdb0d4611cb2ac900
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229969"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel 类

此类提供用于递增和递减变量值的方法。

## <a name="syntax"></a>语法

```
class CComSingleThreadModel
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CComSingleThreadModel：： CriticalSection](#criticalsection)|引用类 `CComFakeCriticalSection` 。|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|引用 `CComSingleThreadModel` 。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CComSingleThreadModel：:D ecrement](#decrement)|递减指定变量的值。 此实现不是线程安全的。|
|[CComSingleThreadModel：：递增](#increment)|递增指定变量的值。 此实现不是线程安全的。|

## <a name="remarks"></a>备注

`CComSingleThreadModel`提供用于递增和递减变量值的方法。 与[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)不同，这些方法不是线程安全的。

通常，使用 `CComSingleThreadModel` **`typedef`** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)这两个名称之一。 每个引用的类都 **`typedef`** 依赖于所使用的线程模型，如下表所示：

|typedef|单线程模型|单元线程模型|自由线程处理模型|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ;M =`CComMultiThreadModel`

`CComSingleThreadModel`本身定义三个 **`typedef`** 名称。 `ThreadModelNoCS`引用 `CComSingleThreadModel` 。 `AutoCriticalSection`和 `CriticalSection` 引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，它提供与获取和释放关键部分的所有权相关的空方法。

## <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

使用时 `CComSingleThreadModel` ， **`typedef`** 名称将 `AutoCriticalSection` 引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>备注

由于不 `CComFakeCriticalSection` 提供临界区，因此它的方法不执行任何操作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含的定义 `AutoCriticalSection` 。 下表显示线程模型类与所引用的临界区类之间的关系 `AutoCriticalSection` ：

|类定义于|引用的类|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了之外 `AutoCriticalSection` ，还可以使用 **`typedef`** 名称[CriticalSection](#criticalsection)。 `AutoCriticalSection`如果要消除 CRT 启动代码，则不应在全局对象或静态类成员中指定。

### <a name="example"></a>示例

请参阅[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel：： CriticalSection

使用时 `CComSingleThreadModel` ， **`typedef`** 名称将 `CriticalSection` 引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>备注

由于不 `CComFakeCriticalSection` 提供临界区，因此它的方法不执行任何操作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含的定义 `CriticalSection` 。 下表显示线程模型类与所引用的临界区类之间的关系 `CriticalSection` ：

|类定义于|引用的类|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了之外 `CriticalSection` ，还可以使用 **`typedef`** 名称[AutoCriticalSection](#autocriticalsection)。 `AutoCriticalSection`如果要消除 CRT 启动代码，则不应在全局对象或静态类成员中指定。

### <a name="example"></a>示例

请参阅[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel：:D ecrement

此静态函数递减*p*指向的变量的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>参数

*h-p*<br/>
中指向要递减的变量的指针。

### <a name="return-value"></a>返回值

减量的结果。

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel：：递增

此静态函数递增*p*指向的变量的值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>参数

*h-p*<br/>
中指向要递增的变量的指针。

### <a name="return-value"></a>返回值

增量的结果。

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

使用时 `CComSingleThreadModel` ， **`typedef`** 名称 `ThreadModelNoCS` 只是引用 `CComSingleThreadModel` 。

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>备注

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含的定义 `ThreadModelNoCS` 。 下表显示线程模型类与引用的类之间的关系 `ThreadModelNoCS` ：

|类定义于|引用的类|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>示例

请参阅[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
