---
title: CComAutoThreadModule 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbef36927598eb0c91185a02030a1c47d4418079
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880032"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule 类
ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class ThreadAllocator = CComSimpleThreadAllocator>  
class CComAutoThreadModule : public CComModule
```  
  
#### <a name="parameters"></a>参数  
 `ThreadAllocator`  
 [in]管理线程选择类。 默认值是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CreateInstance](#createinstance)|选择一个线程，并在关联的单元中创建对象。|  
|[GetDefaultThreads](#getdefaultthreads)|（静态）动态计算基础的处理器数的模块的线程的数。|  
|[Init](#init)|创建模块的线程。|  
|[锁](#lock)|该模块和当前线程上的锁计数递增。|  
|[解锁](#unlock)|减少锁计数模块和当前线程上。|  
  
### <a name="data-members"></a>数据成员  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[dwThreadID](#dwthreadid)|包含当前线程的标识符。|  
|[m_Allocator](#m_allocator)|管理线程选择。|  
|[m_nThreads](#m_nthreads)|包含该模块中的线程数。|  
|[m_pApartments](#m_papartments)|管理模块的单元。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  此类已过时，已被[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)并[CAtlModule](../../atl/reference/catlmodule-class.md)派生的类。 后面的信息适用于较早版本的 atl。  
  
 `CComAutoThreadModule` 派生自[CComModule](../../atl/reference/ccommodule-class.md)实现 Exe 和 Windows 服务的线程池、 单元模型 COM 服务器。 `CComAutoThreadModule` 使用[CComApartment](../../atl/reference/ccomapartment-class.md)管理模块中的每个线程单元。  
  
 派生您的模块从`CComAutoThreadModule`时想要在多个单元中创建对象。 此外必须包括[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)中指定的对象的类定义的宏[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)用作类工厂。  
  
 默认情况下，ATL COM 应用程序向导 （Visual Studio.NET 中的 ATL 项目向导） 将派生您的模块从`CComModule`。 若要使用`CComAutoThreadModule`，修改类定义。 例如：  
  
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
 **标头：** atlbase.h  
  
##  <a name="createinstance"></a>  CComAutoThreadModule::CreateInstance  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>参数  
 *pfnCreateInstance*  
 [in]指向创建程序函数的指针。  
  
 *riid*  
 [in]所请求的接口的 IID。  
  
 *ppvObj*  
 [out]通过标识的接口指针的指针*riid*。 如果该对象不支持此接口， *ppvObj*设置为 NULL。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 选择一个线程，并在关联的单元中创建对象。  
  
##  <a name="dwthreadid"></a>  CComAutoThreadModule::dwThreadID  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
DWORD dwThreadID;
```  
  
### <a name="remarks"></a>备注  
 包含当前线程的标识符。  
  
##  <a name="getdefaultthreads"></a>  CComAutoThreadModule::GetDefaultThreads  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>返回值  
 要在 EXE 模块中创建的线程数。  
  
### <a name="remarks"></a>备注  
 此静态函数动态计算的最大为 EXE 模块，基于处理器的数量的线程数。 默认情况下，此返回值传递给[Init](#init)方法来创建线程。  
  
##  <a name="init"></a>  CComAutoThreadModule::Init  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```  
  
### <a name="parameters"></a>参数  
 *p*  
 [in]指向对象的映射条目的数组的指针。  
  
 *h*  
 [in]传递给 HINSTANCE`DLLMain`或`WinMain`。  
  
 *plibid*  
 [in]一个指向与项目关联的类型库的 LIBID。  
  
 *nThreads*  
 [in]要创建的线程数。 默认情况下*nThreads*是返回的值[GetDefaultThreads](#getdefaultthreads)。  
  
### <a name="remarks"></a>备注  
 初始化数据成员并创建由指定的线程数*nThreads*。  
  
##  <a name="lock"></a>  CComAutoThreadModule::Lock  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>返回值  
 可能是有用的诊断或测试一个值。  
  
### <a name="remarks"></a>备注  
 对模块和当前线程的锁计数执行原子递增。 `CComAutoThreadModule` 使用模块的锁计数来确定任何客户端是否正在访问该模块。 当前线程上的锁计数用于统计目的。  
  
##  <a name="m_allocator"></a>  CComAutoThreadModule::m_Allocator  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
ThreadAllocator  m_Allocator;
```     
  
### <a name="remarks"></a>备注  
 管理线程选择的对象。 默认情况下`ThreadAllocator`类模板参数是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
##  <a name="m_nthreads"></a>  CComAutoThreadModule::m_nThreads  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
int m_nThreads;
```  
  
### <a name="remarks"></a>备注  
 包含 EXE 模块中的线程的数。 当[Init](#init)调用时，`m_nThreads`设置为*nThreads*参数值。 由管理每个线程的关联的单元[CComApartment](../../atl/reference/ccomapartment-class.md)对象。  
  
##  <a name="m_papartments"></a>  CComAutoThreadModule::m_pApartments  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
CComApartment* m_pApartments;
```  
  
### <a name="remarks"></a>备注  
 指向数组[CComApartment](../../atl/reference/ccomapartment-class.md)对象，其中每个管理模块中的某个单元。 数组中的元素数为基础[m_nThreads](#m_nthreads)成员。  
  
##  <a name="unlock"></a>  CComAutoThreadModule::Unlock  
 ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>返回值  
 可能是有用的诊断或测试一个值。  
  
### <a name="remarks"></a>备注  
 对模块和当前线程的锁计数执行原子递减。 `CComAutoThreadModule` 使用模块的锁计数来确定任何客户端是否正在访问该模块。 当前线程上的锁计数用于统计目的。  
  
 当模块锁计数达到零时，模块可以被卸载。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)
