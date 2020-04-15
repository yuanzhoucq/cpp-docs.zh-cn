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
ms.openlocfilehash: 391354c5672cf15c0286491619a13c6005493cfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321066"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule 类

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>参数

*线程定位器*<br/>
[在]管理线程选择的类。 默认值为[CcomSimpleThreadallocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[创建实例](#createinstance)|选择线程，然后在关联的单元中创建对象。|
|[获取默认线程](#getdefaultthreads)|（静态）根据处理器数动态计算模块的线程数。|
|[Init](#init)|创建模块的线程。|
|[Lock](#lock)|增加模块和当前线程上的锁计数。|
|[解 锁](#unlock)|在模块和当前线程上重新分配锁计数。|

### <a name="data-members"></a>数据成员

### <a name="data-members"></a>数据成员

|||
|-|-|
|[dwThreadID](#dwthreadid)|包含当前线程的标识符。|
|[m_Allocator](#m_allocator)|管理线程选择。|
|[m_nThreads](#m_nthreads)|包含模块中的线程数。|
|[m_pApartments](#m_papartments)|管理模块的公寓。|

## <a name="remarks"></a>备注

> [!NOTE]
> 此类已过时，已替换为[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)派生类。 以下信息适用于旧版本的 ATL。

`CComAutoThreadModule`派生自[CComModule，](../../atl/reference/ccommodule-class.md)用于实现用于 EXE 和 Windows 服务的线程池单元式 COM 服务器。 `CComAutoThreadModule`使用[CCom公寓](../../atl/reference/ccomapartment-class.md)管理模块中每个线程的公寓。

从`CComAutoThreadModule`要在多个单元中创建对象时派生模块。 还必须在对象的类定义中包括[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏，以指定[CcomClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)为类工厂。

默认情况下，ATL COM 应用程序向导（Visual Studio .NET 中的 ATL 项目向导）将从`CComModule`派生您的模块。 要使用`CComAutoThreadModule`，请修改类定义。 例如：

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CCom 模块](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThread模块：：创建实例

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>参数

*pfn创建实例*<br/>
[在]指向创建函数的指针。

*riid*<br/>
[在]请求接口的 IID。

*普夫奥比*<br/>
[出]指向*riid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppvObj*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

选择线程，然后在关联的单元中创建对象。

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThread模块：:dwThreadID

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
DWORD dwThreadID;
```

### <a name="remarks"></a>备注

包含当前线程的标识符。

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThread模块：：获取默认线程

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>返回值

要在 EXE 模块中创建的线程数。

### <a name="remarks"></a>备注

此静态函数根据处理器数动态计算 EXE 模块的最大线程数。 默认情况下，此返回值传递给[Init](#init)方法以创建线程。

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThread模块：：Init

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向对象映射条目数组的指针。

*H*<br/>
[在]传递给`DLLMain`或`WinMain`的 HINSTANCE。

*普利比德*<br/>
[在]指向与项目关联的类型库的 LIBID 的指针。

*nThreads*<br/>
[在]要创建的线程数。 默认情况下 *，nThreads*是[GetDefaultThreads](#getdefaultthreads)返回的值。

### <a name="remarks"></a>备注

初始化数据成员并创建*nThreads*指定的线程数。

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThread模块：锁定

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
LONG Lock();
```

### <a name="return-value"></a>返回值

可用于诊断或测试的值。

### <a name="remarks"></a>备注

对模块和当前线程的锁计数执行原子增量。 `CComAutoThreadModule`使用模块锁计数来确定是否有任何客户端正在访问该模块。 当前线程上的锁计数用于统计目的。

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a>CComAutoThread模块：：m_Allocator

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>备注

管理线程选择的对象。 默认情况下，`ThreadAllocator`类模板参数是[CcomSimpleThreadallocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a>CComAutoThread模块：m_nThreads

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
int m_nThreads;
```

### <a name="remarks"></a>备注

包含 EXE 模块中的线程数。 调用[Init](#init)时`m_nThreads`，将设置为*nThreads*参数值。 每个线程的关联单元由[CCom公寓](../../atl/reference/ccomapartment-class.md)对象管理。

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a>CComAutoThread模块：：m_pApartments

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>备注

指向[CCom公寓](../../atl/reference/ccomapartment-class.md)对象数组，每个对象都管理模块中的单元。 数组中的元素数基于[m_nThreads](#m_nthreads)成员。

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThread模块：解锁

从 ATL 7.0`CComAutoThreadModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
LONG Unlock();
```

### <a name="return-value"></a>返回值

可用于诊断或测试的值。

### <a name="remarks"></a>备注

对模块和当前线程的锁计数执行原子减减。 `CComAutoThreadModule`使用模块锁计数来确定是否有任何客户端正在访问该模块。 当前线程上的锁计数用于统计目的。

当模块锁计数达到零时，可以卸载模块。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[模块类](../../atl/atl-module-classes.md)
