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
ms.openlocfilehash: 74fb68eead498685ef252968124368863e27be75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497092"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel 类

`CComMultiThreadModel`提供用于递增和递减变量的值的线程安全方法。

## <a name="syntax"></a>语法

```
class CComMultiThreadModel
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|name|描述|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|引用类[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|引用类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|静止以线程安全的方式递减指定变量的值。|
|[CComMultiThreadModel::Increment](#increment)|静止以线程安全的方式递增指定变量的值。|

## <a name="remarks"></a>备注

通常, 您可以`CComMultiThreadModel`使用以下两种**typedef**名称之一: [CComObjectThreadModel] (CComObjectThreadModel # 或 [CComGlobalsThreadModel] (atl-typedef # CComGlobalsThreadModel。 每个**typedef**引用的类取决于所使用的线程模型, 如下表所示:

|typedef|单线程|单元线程处理|自由线程处理|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M= `CComMultiThreadModel`

`CComMultiThreadModel`本身定义了三个**typedef**名称。 `AutoCriticalSection`和`CriticalSection`引用类, 它们提供获取和释放关键部分的所有权的方法。 `ThreadModelNoCS`引用类 [CComMultiThreadModelNoCS (CComMultiThreadModelNoCS-class.md)。

## <a name="requirements"></a>要求

**标头:** atlbase.h

##  <a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection

使用`CComMultiThreadModel`时, **typedef**名称`AutoCriticalSection`引用类[CComAutoCriticalSection](ccomautocriticalsection-class.md), 这提供了获取和释放关键节对象的所有权的方法。

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>备注

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)也包含的`AutoCriticalSection`定义。 下表显示线程模型类与所引用`AutoCriticalSection`的临界区类之间的关系:

|类定义于|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了之外`AutoCriticalSection`, 还可以使用**typedef**名称[CriticalSection](#criticalsection)。 如果要消除 CRT `AutoCriticalSection`启动代码, 则不应在全局对象或静态类成员中指定。

### <a name="example"></a>示例

下面的代码在[CComObjectRootEx](ccomobjectrootex-class.md)后建模, 并演示`AutoCriticalSection`在线程环境中使用。

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

下表显示了`InternalAddRef`和`Lock`方法的结果, 具体取决于应用程序`ThreadModel`使用的模板参数和线程模型:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|方法|单个或单元线程处理|自由线程处理|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是线程安全的。|增量是线程安全的。|
|`Lock`|不执行任何操作;没有要锁定的关键部分。|临界区已锁定。|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel:: ThreadModelNoCS

|方法|单个或单元线程处理|自由线程处理|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是线程安全的。|增量是线程安全的。|
|`Lock`|不执行任何操作;没有要锁定的关键部分。|不执行任何操作;没有要锁定的关键部分。|

##  <a name="criticalsection"></a>CComMultiThreadModel:: CriticalSection

使用`CComMultiThreadModel`时, **typedef**名称`CriticalSection`引用类[CComCriticalSection](ccomcriticalsection-class.md), 这提供了获取和释放关键节对象的所有权的方法。

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>备注

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)也包含的`CriticalSection`定义。 下表显示线程模型类与所引用`CriticalSection`的临界区类之间的关系:

|类定义于|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了之外`CriticalSection`, 还可以使用**typedef**名称[AutoCriticalSection](#autocriticalsection)。 如果要消除 CRT `AutoCriticalSection`启动代码, 则不应在全局对象或静态类成员中指定。

### <a name="example"></a>示例

请参阅[CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection)。

##  <a name="decrement"></a>CComMultiThreadModel::D ecrement

此静态函数调用 Win32 函数[InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), 该函数递减*p*指向的变量的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>参数

*p*<br/>
中指向要递减的变量的指针。

### <a name="return-value"></a>返回值

如果减量的结果为 0, 则`Decrement`返回0。 如果减量的结果为非零值, 则返回值也为非零值, 但可能不等于减量结果。

### <a name="remarks"></a>备注

`InterlockedDecrement`防止多个线程同时使用此变量。

##  <a name="increment"></a>CComMultiThreadModel:: 递增

此静态函数调用 Win32 函数[InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), 该函数递增*p*指向的变量的值。

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>参数

*p*<br/>
中指向要递增的变量的指针。

### <a name="return-value"></a>返回值

如果增量的结果是 0, 则`Increment`返回0。 如果增量的结果为非零值, 则返回值也为非零值, 但可能不等于增量的结果。

### <a name="remarks"></a>备注

`InterlockedIncrement`防止多个线程同时使用此变量。

##  <a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS

使用`CComMultiThreadModel`时, **typedef**名称`ThreadModelNoCS`引用类[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>备注

`CComMultiThreadModelNoCS`提供用于递增和递减变量的线程安全方法;但是, 它不提供关键部分。

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)和`CComMultiThreadModelNoCS`还包含的`ThreadModelNoCS`定义。 下表显示线程模型类与引用`ThreadModelNoCS`的类之间的关系:

|类定义于|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>示例

请参阅[CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection)。

## <a name="see-also"></a>请参阅

[CComSingleThreadModel 类](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection 类](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection 类](ccomcriticalsection-class.md)<br/>
[类概述](../atl-class-overview.md)
