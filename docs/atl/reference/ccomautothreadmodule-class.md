---
title: CComAutoThreadModule 类
ms.date: 11/04/2016
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: 9b0fa685bf9a7de94b158bd62b00161c1b58562d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866168"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule 类

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>parameters

*ThreadAllocator*<br/>
中管理线程选择的类。 默认值为[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CreateInstance](#createinstance)|选择一个线程，然后在关联单元中创建对象。|
|[GetDefaultThreads](#getdefaultthreads)|静止基于处理器数量动态计算模块的线程数。|
|[Init](#init)|创建模块的线程。|
|[住](#lock)|递增模块和当前线程上的锁计数。|
|[解锁](#unlock)|递减模块和当前线程上的锁计数。|

### <a name="data-members"></a>数据成员

### <a name="data-members"></a>数据成员

|||
|-|-|
|[dwThreadID](#dwthreadid)|包含当前线程的标识符。|
|[m_Allocator](#m_allocator)|管理线程选择。|
|[m_nThreads](#m_nthreads)|包含模块中的线程数。|
|[m_pApartments](#m_papartments)|管理模块的单元。|

## <a name="remarks"></a>备注

> [!NOTE]
>  此类已过时，已替换为[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)派生类。 下面的信息适用于更早版本的 ATL。

`CComAutoThreadModule` 从[CComModule](../../atl/reference/ccommodule-class.md)派生，以实现 Exe 和 Windows 服务的线程池的单元模型 COM 服务器。 `CComAutoThreadModule` 使用[CComApartment](../../atl/reference/ccomapartment-class.md)为模块中的每个线程管理单元。

如果要在多个单元中创建对象，请从 `CComAutoThreadModule` 派生模块。 还必须在对象的类定义中包含[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏，才能指定[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)作为类工厂。

默认情况下，ATL COM 向导（Visual Studio .NET 中的 ATL 项目向导）将从 `CComModule`派生你的模块。 若要使用 `CComAutoThreadModule`，请修改类定义。 例如：

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="createinstance"></a>CComAutoThreadModule：： CreateInstance

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>parameters

*pfnCreateInstance*<br/>
中指向 creator 函数的指针。

*riid*<br/>
中所请求的接口的 IID。

*ppvObj*<br/>
弄指向由*riid*标识的接口指针的指针。 如果对象不支持此接口，则将*ppvObj*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

选择一个线程，然后在关联单元中创建对象。

##  <a name="dwthreadid"></a>CComAutoThreadModule：:d wThreadID

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
DWORD dwThreadID;
```

### <a name="remarks"></a>备注

包含当前线程的标识符。

##  <a name="getdefaultthreads"></a>CComAutoThreadModule：： GetDefaultThreads

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>返回值

要在 EXE 模块中创建的线程数。

### <a name="remarks"></a>备注

此静态函数根据处理器数量动态计算 EXE 模块的最大线程数。 默认情况下，此返回值将传递给[Init](#init)方法以创建线程。

##  <a name="init"></a>CComAutoThreadModule：： Init

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>parameters

*p*<br/>
中指向对象映射项的数组的指针。

h<br/>
中传递给 `DLLMain` 或 `WinMain`的 HINSTANCE。

*plibid*<br/>
中一个指针，指向与项目关联的类型库的 LIBID。

*nThreads*<br/>
中要创建的线程数。 默认情况下， *nThreads*是[GetDefaultThreads](#getdefaultthreads)返回的值。

### <a name="remarks"></a>备注

初始化数据成员，并创建*nThreads*指定的线程数。

##  <a name="lock"></a>CComAutoThreadModule：： Lock

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
LONG Lock();
```

### <a name="return-value"></a>返回值

可能对诊断或测试有用的值。

### <a name="remarks"></a>备注

对模块和当前线程的锁计数执行原子增量。 `CComAutoThreadModule` 使用模块锁计数来确定是否有任何客户端访问该模块。 当前线程上的锁计数用于统计目的。

##  <a name="m_allocator"></a>CComAutoThreadModule：： m_Allocator

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>备注

管理线程选择的对象。 默认情况下，`ThreadAllocator` 类模板参数为[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

##  <a name="m_nthreads"></a>CComAutoThreadModule：： m_nThreads

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
int m_nThreads;
```

### <a name="remarks"></a>备注

包含 EXE 模块中的线程数。 调用[Init](#init)时，`m_nThreads` 设置为*nThreads*参数值。 每个线程的关联单元由[CComApartment](../../atl/reference/ccomapartment-class.md)对象管理。

##  <a name="m_papartments"></a>CComAutoThreadModule：： m_pApartments

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>备注

指向[CComApartment](../../atl/reference/ccomapartment-class.md)对象的数组，其中每个对象都管理该模块中的一个单元。 数组中的元素数基于[m_nThreads](#m_nthreads)成员。

##  <a name="unlock"></a>CComAutoThreadModule：： Unlock

从 ATL 7.0，`CComAutoThreadModule` 已过时：有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
LONG Unlock();
```

### <a name="return-value"></a>返回值

可能对诊断或测试有用的值。

### <a name="remarks"></a>备注

对模块和当前线程的锁计数执行原子减量。 `CComAutoThreadModule` 使用模块锁计数来确定是否有任何客户端访问该模块。 当前线程上的锁计数用于统计目的。

当模块锁计数达到零时，可以卸载该模块。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[Module 类](../../atl/atl-module-classes.md)
