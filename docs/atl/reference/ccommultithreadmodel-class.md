---
title: CComMultiThreadModel 类
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
ms.openlocfilehash: 6b77efffca127c79c665cb8dedb916b0874de038
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290724"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel 类

`CComMultiThreadModel` 提供用于递增和递减变量的值的线程安全方法。

## <a name="syntax"></a>语法

```
class CComMultiThreadModel
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|引用类[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|引用类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|（静态）递减指定变量以线程安全的方式的值。|
|[CComMultiThreadModel::Increment](#increment)|（静态）以线程安全的方式递增指定变量的值。|

## <a name="remarks"></a>备注

通常情况下，使用`CComMultiThreadModel`通过两个之一**typedef**名称、 任一 [CComObjectThreadModel] (atl typedefs.md #ccomobjectthreadmodel 或 [CComGlobalsThreadModel] (atl typedefs.md #ccomglobalsthreadmodel。 每个引用的类**typedef** ，所使用的线程处理模型取决于下表中所示：

|typedef|单个线程处理|单元线程处理|自由线程处理|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M= `CComMultiThreadModel`

`CComMultiThreadModel` 本身定义三个**typedef**名称。 `AutoCriticalSection` 和`CriticalSection`引用类提供方法用于获取并释放关键节的所有权。 `ThreadModelNoCS` 引用类 [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md)。

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection

使用时`CComMultiThreadModel`，则**typedef**名称`AutoCriticalSection`引用类[CComAutoCriticalSection](ccomautocriticalsection-class.md)，其提供方法用于获取并释放关键节的所有权对象。

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>备注

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)并[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)还包含定义`AutoCriticalSection`。 下表显示了线程处理模型类与所引用的关键部分类之间的关系`AutoCriticalSection`:

|在中定义类|引用类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了`AutoCriticalSection`，可以使用**typedef**名称[CriticalSection](#criticalsection)。 不应指定`AutoCriticalSection`全局对象或如果你想要消除 CRT 启动代码的静态类成员中。

### <a name="example"></a>示例

下面的代码模仿[CComObjectRootEx](ccomobjectrootex-class.md)，并演示`AutoCriticalSection`线程环境中正在使用。

```cpp
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```

下表显示的结果`InternalAddRef`并`Lock`方法，具体取决于`ThreadModel`模板参数和应用程序使用的线程模型：

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|方法|单个或单元线程处理|自由线程处理|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是线程安全的。|增量是线程安全的。|
|`Lock`|没有执行任何操作;没有锁定关键节。|锁定关键部分。|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|方法|单个或单元线程处理|自由线程处理|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是线程安全的。|增量是线程安全的。|
|`Lock`|没有执行任何操作;没有锁定关键节。|没有执行任何操作;没有锁定关键节。|

##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection

使用时`CComMultiThreadModel`，则**typedef**名称`CriticalSection`引用类[CComCriticalSection](ccomcriticalsection-class.md)，其中提供用于获取并释放关键节对象的所有权的方法。

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>备注

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)并[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)还包含定义`CriticalSection`。 下表显示了线程处理模型类与所引用的关键部分类之间的关系`CriticalSection`:

|在中定义类|引用类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了`CriticalSection`，可以使用**typedef**名称[AutoCriticalSection](#autocriticalsection)。 不应指定`AutoCriticalSection`全局对象或如果你想要消除 CRT 启动代码的静态类成员中。

### <a name="example"></a>示例

请参阅[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。

##  <a name="decrement"></a>  CComMultiThreadModel::Decrement

此静态函数将调用 Win32 函数[InterlockedDecrement](/windows/desktop/api/winbase/nf-winbase-interlockeddecrement)，指向变量的值的递减*p*。

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>参数

*p*<br/>
[in]指向要递减的变量。

### <a name="return-value"></a>返回值

如果结果递减为 0，则`Decrement`返回 0。 递减的结果为非零值，如果返回值也为非零值，但可能不是递减的结果。

### <a name="remarks"></a>备注

`InterlockedDecrement` 防止多个线程同时使用此变量。

##  <a name="increment"></a>  CComMultiThreadModel::Increment

此静态函数将调用 Win32 函数[InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement)，指向的变量的值时都会增加*p*。

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>参数

*p*<br/>
[in]指向要递增的变量。

### <a name="return-value"></a>返回值

如果增量结果为 0，则`Increment`返回 0。 如果非零值的增量结果，返回值也为非零值，但不是与相同的增量结果。

### <a name="remarks"></a>备注

`InterlockedIncrement` 防止多个线程同时使用此变量。

##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS

使用时`CComMultiThreadModel`，则**typedef**名称`ThreadModelNoCS`引用类[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>备注

`CComMultiThreadModelNoCS` 提供用于递增和递减变量，例如： 线程安全方法但是，它不提供关键部分。

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)并`CComMultiThreadModelNoCS`还包含定义`ThreadModelNoCS`。 下表显示了线程处理模型类与所引用的类之间的关系`ThreadModelNoCS`:

|在中定义类|引用类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>示例

请参阅[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。

## <a name="see-also"></a>请参阅

[CComSingleThreadModel 类](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection 类](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection 类](ccomcriticalsection-class.md)<br/>
[类概述](../atl-class-overview.md)
