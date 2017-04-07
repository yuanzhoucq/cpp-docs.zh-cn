---
title: "CComAutoThreadModule 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 8e3ad5333d684daff5d8baf462ae805ef8b4b51d
ms.lasthandoff: 03/31/2017

---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule 类
ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
|[CreateInstance](#createinstance)|选择一个线程，然后在关联的单元内创建一个对象。|  
|[GetDefaultThreads](#getdefaultthreads)|（静态）动态计算模块基于的处理器数量的线程数。|  
|[Init](#init)|创建模块的线程。|  
|[锁](#lock)|递增模块和当前线程上的锁计数。|  
|[解锁](#unlock)|减少锁计数和当前线程上的模块。|  
  
### <a name="data-members"></a>数据成员  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[dwThreadID](#dwthreadid)|包含当前线程的标识符。|  
|[m_Allocator](#m_allocator)|管理线程所选内容。|  
|[m_nThreads](#m_nthreads)|包含模块中的线程的数。|  
|[m_pApartments](#m_papartments)|管理模块的单元。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  此类已过时，已由[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)派生类。 后面的信息是用于较早版本的 atl。  
  
 `CComAutoThreadModule`派生自[CComModule](../../atl/reference/ccommodule-class.md)实现为 Exe 和 Windows 服务的线程放入池中，单元模型 COM 服务器。 `CComAutoThreadModule`使用[CComApartment](../../atl/reference/ccomapartment-class.md)管理模块中的每个线程单元。  
  
 派生您的模块从`CComAutoThreadModule`如果想要在多个单元中创建对象。 你还必须包括[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)中对象的类定义，以指定宏[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)作为类工厂。  
  
 默认情况下，ATL COM 应用程序向导 （ATL 项目向导 Visual Studio.NET 中） 将派生您的模块从`CComModule`。 若要使用`CComAutoThreadModule`，修改的类定义。 例如：  
  
 [!code-cpp[NVC_ATL_AxHost # 2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `IAtlAutoThreadModule`  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 [CComModule](../../atl/reference/ccommodule-class.md)  
  
 `CComAutoThreadModule`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="createinstance"></a>CComAutoThreadModule::CreateInstance  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>参数  
 *pfnCreateInstance*  
 [in]指向创建程序函数的指针。  
  
 `riid`  
 [in]所请求的接口的 IID。  
  
 `ppvObj`  
 [out]指向由标识的接口指针的指针`riid`。 如果对象不支持此接口，`ppvObj`设置为 NULL。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 选择一个线程，然后在关联的单元内创建一个对象。  
  
##  <a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
DWORD dwThreadID;
```  
  
### <a name="remarks"></a>备注  
 包含当前线程的标识符。  
  
##  <a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>返回值  
 要在 EXE 模块中创建的线程数。  
  
### <a name="remarks"></a>备注  
 此静态函数动态计算最大为 EXE 模块，基于的处理器数量的线程数。 默认情况下，此返回值传递给[Init](#init)方法来创建多个线程。  
  
##  <a name="init"></a>CComAutoThreadModule::Init  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向对象的映射条目的数组的指针。  
  
 `h`  
 [in]`HINSTANCE`传递给**DLLMain**或`WinMain`。  
  
 `plibid`  
 [in]指向与项目关联的类型库的 LIBID 的指针。  
  
 `nThreads`  
 [in]要创建的线程数。 默认情况下，`nThreads`是通过返回的值[GetDefaultThreads](#getdefaultthreads)。  
  
### <a name="remarks"></a>备注  
 初始化数据成员并创建由指定的线程数`nThreads`。  
  
##  <a name="lock"></a>CComAutoThreadModule::Lock  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断或测试。  
  
### <a name="remarks"></a>备注  
 在模块和当前线程的锁计数上执行原子递增。 `CComAutoThreadModule`使用的模块锁计数来确定任何客户端是否正在访问该模块。 用于统计目的使用当前线程上的锁计数。  
  
##  <a name="m_allocator"></a>CComAutoThreadModule::m_Allocator  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
ThreadAllocator  m_Allocator;
```     
  
### <a name="remarks"></a>备注  
 管理线程选择的对象。 默认情况下，`ThreadAllocator`类模板参数是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
##  <a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
int m_nThreads;
```  
  
### <a name="remarks"></a>备注  
 包含 EXE 模块中的线程的数。 当[Init](#init)调用时，`m_nThreads`设置为`nThreads`参数值。 每个线程关联的单元由[CComApartment](../../atl/reference/ccomapartment-class.md)对象。  
  
##  <a name="m_papartments"></a>CComAutoThreadModule::m_pApartments  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
CComApartment* m_pApartments;
```  
  
### <a name="remarks"></a>备注  
 指向数组的[CComApartment](../../atl/reference/ccomapartment-class.md)对象，其中每个管理模块中的某个单元。 数组中元素的数目取决于[m_nThreads](#m_nthreads)成员。  
  
##  <a name="unlock"></a>CComAutoThreadModule::Unlock  
 ATL 7.0 截至`CComAutoThreadModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断或测试。  
  
### <a name="remarks"></a>备注  
 在模块和当前线程的锁计数上执行原子递减。 `CComAutoThreadModule`使用的模块锁计数来确定任何客户端是否正在访问该模块。 用于统计目的使用当前线程上的锁计数。  
  
 当模块锁计数达到零时，模块可以被卸载。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)

