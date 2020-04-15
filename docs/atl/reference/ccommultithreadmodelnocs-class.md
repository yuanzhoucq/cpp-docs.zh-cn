---
title: CComMultiThreadModelNoCS 类
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: 4d41ffcfccbd7ef65ed86df79bffec1209a88cd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327655"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS 类

`CComMultiThreadModelNoCS`提供线程安全方法，用于递增和递减变量的值，而无需关键截面锁定或解锁功能。

## <a name="syntax"></a>语法

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CCom 多线程模型NoCS：：自动临界部分](#autocriticalsection)|引用类[CComFake 临界节](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CCom 多线程模型NoCS：：关键部分](#criticalsection)|引用类`CComFakeCriticalSection`。|
|[CCom 多线程模型NoCS：：线程模型NoCS](#threadmodelnocs)|引用类`CComMultiThreadModelNoCS`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom 多线程模型NoCS：:D](#decrement)|（静态）以线程安全的方式声明指定变量的值。|
|[CCom 多线程模型NoCS：：增量](#increment)|（静态）以线程安全的方式递增指定变量的值。|

## <a name="remarks"></a>备注

`CComMultiThreadModelNoCS`与[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)类似，因为它提供了用于递增和递减变量的线程安全方法。 但是，当您通过`CComMultiThreadModelNoCS`引用关键节类时，方法如`Lock`和`Unlock`将不执行任何操作。

通常，您可以通过`CComMultiThreadModelNoCS``ThreadModelNoCS`**typedef**名称使用。 此**类型def**在`CComMultiThreadModelNoCS`中`CComMultiThreadModel`定义 ， 和[CCom 单线程模型](../../atl/reference/ccomsinglethreadmodel-class.md)。

> [!NOTE]
> 全局**类型定义**名称[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)和[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) `CComMultiThreadModelNoCS`不引用 。

除了`ThreadModelNoCS`之外，`CComMultiThreadModelNoCS`定义`AutoCriticalSection`和`CriticalSection`。 后两**个类型定义**名称引用[CComFake临界节](../../atl/reference/ccomfakecriticalsection-class.md)，它提供了与获取和释放关键部分相关的空方法。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CCom 多线程模型NoCS：：自动临界部分

使用`CComMultiThreadModelNoCS`时 **，typedef** `AutoCriticalSection`名称引用类[CComFake临界节](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>备注

因为`CComFakeCriticalSection`不提供关键部分，因此其方法不执行任何操作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CCom 单线程模型](../../atl/reference/ccomsinglethreadmodel-class.md)还包含`AutoCriticalSection`的定义。 下表显示了线程模型类与 引用`AutoCriticalSection`的关键节类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

除 之外`AutoCriticalSection`，还可以使用**typedef**名称["临界节](#criticalsection)"。 如果要消除 CRT 启动代码，不应在全局对象或静态类成员中指定`AutoCriticalSection`。

### <a name="example"></a>示例

请参阅[CCom 多线程模型：：自动临界节](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CCom 多线程模型NoCS：：关键部分

使用`CComMultiThreadModelNoCS`时 **，typedef** `CriticalSection`名称引用类[CComFake临界节](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>备注

因为`CComFakeCriticalSection`不提供关键部分，因此其方法不执行任何操作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CCom 单线程模型](../../atl/reference/ccomsinglethreadmodel-class.md)还包含`CriticalSection`的定义。 下表显示了线程模型类与 引用`CriticalSection`的关键节类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

除了 之外`CriticalSection`，还可以使用**typedef**名称`AutoCriticalSection`。 如果要消除 CRT 启动代码，不应在全局对象或静态类成员中指定`AutoCriticalSection`。

### <a name="example"></a>示例

请参阅[CCom 多线程模型：：自动临界节](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CCom 多线程模型NoCS：:D

此静态函数调用 Win32 函数[互锁声明](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)，它递减*p*指向的变量的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向要递减的变量的指针。

### <a name="return-value"></a>返回值

如果递减的结果为 0，则`Decrement`返回 0。 如果递减的结果为非零，则返回值也是非零，但可能不等于递减的结果。

### <a name="remarks"></a>备注

**互锁的"声明"** 可防止多个线程同时使用此变量。

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CCom 多线程模型NoCS：：增量

此静态函数调用 Win32 函数[互锁增量](/windows/win32/api/winnt/nf-winnt-interlockedincrement)，它递增*p*指向的变量的值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向要递增的变量的指针。

### <a name="return-value"></a>返回值

如果增量的结果为 0，则**增量**返回 0。 如果增量的结果是非零，则返回值也是非零，但可能不等于增量的结果。

### <a name="remarks"></a>备注

**互锁增量**可防止多个线程同时使用此变量。

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CCom 多线程模型NoCS：：线程模型NoCS

使用`CComMultiThreadModelNoCS`时 **，typedef** `ThreadModelNoCS`名称仅`CComMultiThreadModelNoCS`引用 。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>备注

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CCom 单线程模型](../../atl/reference/ccomsinglethreadmodel-class.md)还包含`ThreadModelNoCS`的定义。 下表显示了线程模型类与 引用的`ThreadModelNoCS`类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

请注意`ThreadModelNoCS`，中的`CComMultiThreadModelNoCS`定义提供了 与 和`CComMultiThreadModel``CComSingleThreadModel`的对称性。 例如，假设声明的以下`CComMultiThreadModel::AutoCriticalSection`**typedef**中的示例代码 ：

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

无论为`ThreadModel`（如`CComMultiThreadModelNoCS`） 指定的类`_ThreadModel`如何，都会相应地解析。

### <a name="example"></a>示例

请参阅[CCom 多线程模型：：自动临界节](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
