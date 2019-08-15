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
ms.openlocfilehash: 01c7f953b6b8916394ee4c2b5b27cf84af52b920
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497089"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS 类

`CComMultiThreadModelNoCS`提供用于递增和递减变量的值的线程安全方法, 而不包含锁定或解锁功能的关键部分。

## <a name="syntax"></a>语法

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|name|描述|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|引用类`CComFakeCriticalSection`。|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|引用类`CComMultiThreadModelNoCS`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|静止以线程安全的方式递减指定变量的值。|
|[CComMultiThreadModelNoCS::Increment](#increment)|静止以线程安全的方式递增指定变量的值。|

## <a name="remarks"></a>备注

`CComMultiThreadModelNoCS`类似于[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) , 因为它提供了用于递增和递减变量的线程安全方法。 但是, 当通过`CComMultiThreadModelNoCS`引用关键节类时, 方法`Lock` (如和`Unlock` ) 将不执行任何操作。

通常, 可以`ThreadModelNoCS`通过`CComMultiThreadModelNoCS` **typedef**名称使用。 此**typedef**是在、 `CComMultiThreadModelNoCS` `CComMultiThreadModel`和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)中定义的。

> [!NOTE]
>  全局**typedef**名称[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)和[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)不引用`CComMultiThreadModelNoCS`。

除了之外`ThreadModelNoCS`, `CComMultiThreadModelNoCS`还定义`AutoCriticalSection`了`CriticalSection`和。 后两个**typedef**名称引用[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), 它提供与获取和释放关键部分关联的空方法。

## <a name="requirements"></a>要求

**标头:** atlbase。h

##  <a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

使用`CComMultiThreadModelNoCS`时, **typedef**名称`AutoCriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>备注

由于`CComFakeCriticalSection`不提供临界区, 因此它的方法不执行任何操作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含的`AutoCriticalSection`定义。 下表显示线程模型类与所引用`AutoCriticalSection`的临界区类之间的关系:

|类定义于|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

除了之外`AutoCriticalSection`, 还可以使用**typedef**名称[CriticalSection](#criticalsection)。 如果要消除 CRT `AutoCriticalSection`启动代码, 则不应在全局对象或静态类成员中指定。

### <a name="example"></a>示例

请参阅[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

##  <a name="criticalsection"></a>CComMultiThreadModelNoCS:: CriticalSection

使用`CComMultiThreadModelNoCS`时, **typedef**名称`CriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>备注

由于`CComFakeCriticalSection`不提供临界区, 因此它的方法不执行任何操作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含的`CriticalSection`定义。 下表显示线程模型类与所引用`CriticalSection`的临界区类之间的关系:

|类定义于|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

除了之外`CriticalSection`, 还可以使用**typedef**名称`AutoCriticalSection`。 如果要消除 CRT `AutoCriticalSection`启动代码, 则不应在全局对象或静态类成员中指定。

### <a name="example"></a>示例

请参阅[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

##  <a name="decrement"></a>CComMultiThreadModelNoCS::D ecrement

此静态函数调用 Win32 函数[InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), 该函数递减*p*指向的变量的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
中指向要递减的变量的指针。

### <a name="return-value"></a>返回值

如果减量的结果为 0, 则`Decrement`返回0。 如果减量的结果为非零值, 则返回值也为非零值, 但可能不等于减量结果。

### <a name="remarks"></a>备注

**InterlockedDecrement**防止多个线程同时使用此变量。

##  <a name="increment"></a>CComMultiThreadModelNoCS:: 递增

此静态函数调用 Win32 函数[InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), 该函数递增*p*指向的变量的值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
中指向要递增的变量的指针。

### <a name="return-value"></a>返回值

如果增量的结果是 0, 则**增量**返回0。 如果增量的结果为非零值, 则返回值也为非零值, 但可能不等于增量的结果。

### <a name="remarks"></a>备注

**InterlockedIncrement**防止多个线程同时使用此变量。

##  <a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

使用`CComMultiThreadModelNoCS`时, **typedef**名称`ThreadModelNoCS`只引用。 `CComMultiThreadModelNoCS`

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>备注

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含的`ThreadModelNoCS`定义。 下表显示线程模型类与引用`ThreadModelNoCS`的类之间的关系:

|类定义于|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

请注意, `ThreadModelNoCS`中`CComMultiThreadModelNoCS`的定义提供与`CComMultiThreadModel`和`CComSingleThreadModel`的对称。 例如, 假设中`CComMultiThreadModel::AutoCriticalSection`的示例代码声明了以下**typedef**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

无论为指定的类 ( `ThreadModel` `CComMultiThreadModelNoCS`例如), `_ThreadModel`都将相应地进行解析。

### <a name="example"></a>示例

请参阅[CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
