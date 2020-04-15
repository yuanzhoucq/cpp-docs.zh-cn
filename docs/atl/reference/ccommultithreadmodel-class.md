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
ms.openlocfilehash: 7ef803439d2d683633e8f9c00810542dd787541e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327674"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel 类

`CComMultiThreadModel`提供线程安全方法，用于递增和递减变量的值。

## <a name="syntax"></a>语法

```
class CComMultiThreadModel
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CCom 多线程模型：：自动临界部分](#autocriticalsection)|引用类[CComAuto临界节](../../atl/reference/ccomautocriticalsection-class.md)。|
|[CCom 多线程模型：：关键部分](#criticalsection)|引用类[CCom临界节](../../atl/reference/ccomcriticalsection-class.md)。|
|[CCom 多线程模型：：线程模型NoCS](#threadmodelnocs)|引用类[CCom 多线程模型NoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom 多线程模型：:D](#decrement)|（静态）以线程安全的方式声明指定变量的值。|
|[CCom 多线程模型：增量](#increment)|（静态）以线程安全的方式递增指定变量的值。|

## <a name="remarks"></a>备注

通常，您可以通过两`CComMultiThreadModel`个**类型定义**名称之一使用，即 [CcomObjectThreadModel]（atl typedefs.md_ccomobjectthreadmodel 或 [CcomGlobalsThreadModel]（atl-typedefs.md_ccomglobalsthreadmodel）。 每个**typedef**引用的类取决于所使用的线程模型，如下表所示：

|typedef|单线程|公寓线程|免费线程|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`;M#`CComMultiThreadModel`

`CComMultiThreadModel`本身定义三**个类型定义**名称。 `AutoCriticalSection`和`CriticalSection`提供获取和释放关键部分所有权的方法的引用类。 `ThreadModelNoCS`引用类 _CComMultiThreadModelNoCS（ccom 多线程模型-class.md）。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CCom 多线程模型：：自动临界部分

使用`CComMultiThreadModel`时 **，typedef** `AutoCriticalSection`名称引用类[CComAuto临界节](ccomautocriticalsection-class.md)，它提供了获取和释放关键节对象所有权的方法。

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>备注

[CCom 单线程模型](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)还包含`AutoCriticalSection`的定义。 下表显示了线程模型类与 引用`AutoCriticalSection`的关键节类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除 之外`AutoCriticalSection`，还可以使用**typedef**名称["临界节](#criticalsection)"。 如果要消除 CRT 启动代码，不应在全局对象或静态类成员中指定`AutoCriticalSection`。

### <a name="example"></a>示例

以下代码以[CcomObjectRootEx](ccomobjectrootex-class.md)建模，并演示`AutoCriticalSection`在线程环境中使用。

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

下表显示了`InternalAddRef`和`Lock`方法的结果，具体取决于`ThreadModel`模板参数和应用程序使用的线程模型：

### <a name="threadmodel--ccomobjectthreadmodel"></a>线程模型 = CComobject 线程模型

|方法|单线程或公寓线程|免费线程|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是线程安全的。|增量是线程安全的。|
|`Lock`|什么都不做;没有要锁定的关键部分。|关键部分已锁定。|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>线程模型 = CComobject 线程模型：：线程模型NoCS

|方法|单线程或公寓线程|免费线程|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是线程安全的。|增量是线程安全的。|
|`Lock`|什么都不做;没有要锁定的关键部分。|什么都不做;没有要锁定的关键部分。|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CCom 多线程模型：：关键部分

使用`CComMultiThreadModel`时 **，typedef** `CriticalSection`名称引用类[CCom临界节](ccomcriticalsection-class.md)，它提供了获取和释放关键节对象所有权的方法。

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>备注

[CCom 单线程模型](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)还包含`CriticalSection`的定义。 下表显示了线程模型类与 引用`CriticalSection`的关键节类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除 之外`CriticalSection`，还可以使用**typedef**名称[Auto临界节](#autocriticalsection)。 如果要消除 CRT 启动代码，不应在全局对象或静态类成员中指定`AutoCriticalSection`。

### <a name="example"></a>示例

请参阅[CCom 多线程模型：：自动临界节](#autocriticalsection)。

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CCom 多线程模型：:D

此静态函数调用 Win32 函数[互锁声明](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)，它递减*p*指向的变量的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向要递减的变量的指针。

### <a name="return-value"></a>返回值

如果递减的结果为 0，则`Decrement`返回 0。 如果递减的结果为非零，则返回值也是非零，但可能不等于递减的结果。

### <a name="remarks"></a>备注

`InterlockedDecrement`防止多个线程同时使用此变量。

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CCom 多线程模型：增量

此静态函数调用 Win32 函数[互锁增量](/windows/win32/api/winnt/nf-winnt-interlockedincrement)，它递增*p*指向的变量的值。

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向要递增的变量的指针。

### <a name="return-value"></a>返回值

如果增量的结果为 0，则`Increment`返回 0。 如果增量的结果是非零，则返回值也是非零，但可能不等于增量的结果。

### <a name="remarks"></a>备注

`InterlockedIncrement`防止多个线程同时使用此变量。

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CCom 多线程模型：：线程模型NoCS

使用`CComMultiThreadModel`时 **，typedef** `ThreadModelNoCS`名称引用类[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>备注

`CComMultiThreadModelNoCS`提供线程安全方法，用于递增和递减变量;但是，它不提供关键部分。

[CComSingleThreadModel，](ccomsinglethreadmodel-class.md)并`CComMultiThreadModelNoCS`包含 的定义`ThreadModelNoCS`。 下表显示了线程模型类与 引用的`ThreadModelNoCS`类之间的关系：

|类定义在|引用的类|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>示例

请参阅[CCom 多线程模型：：自动临界节](#autocriticalsection)。

## <a name="see-also"></a>另请参阅

[CComSingleThreadModel 类](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection 类](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection 类](ccomcriticalsection-class.md)<br/>
[类概述](../atl-class-overview.md)
