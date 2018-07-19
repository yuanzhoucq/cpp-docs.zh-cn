---
title: CAtlDllModuleT 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86fae3c77f06ab7dd3fb2104eda928c1a72b8cc3
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883539"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT 类
此类表示对 dll 的模块。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类派生自`CAtlDllModuleT`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|构造函数。|  
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|测试是否可以卸载 DLL。|  
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|返回类工厂。|  
|[CAtlDllModuleT::DllMain](#dllmain)|动态链接库 (DLL) 可选入口点。|  
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|将条目添加到系统注册表的 DLL 中的对象。|  
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|在 DLL 中的对象在系统注册表中移除项。|  
|[CAtlDllModuleT::GetClassObject](#getclassobject)|返回类工厂。 通过调用[DllGetClassObject](#dllgetclassobject)。|  
  
## <a name="remarks"></a>备注  
 `CAtlDllModuleT` 表示动态链接库 (DLL) 的模块，并提供使用 DLL 的所有项目的函数。 此专用化[CAtlModuleT](../../atl/reference/catlmodulet-class.md)类包括支持进行注册。  
  
 在 ATL 中的模块的详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="catldllmodulet"></a>  CAtlDllModuleT::CAtlDllModuleT  
 构造函数。  
  
```
CAtlDllModuleT() throw();
```  
  
##  <a name="dtor"></a>  CAtlDllModuleT:: ~ CAtlDllModuleT  
 析构函数。  
  
```
~CAtlDllModuleT() throw();
```  
  
##  <a name="dllcanunloadnow"></a>  CAtlDllModuleT::DllCanUnloadNow  
 测试是否可以卸载 DLL。  
  
```
HRESULT DllCanUnloadNow() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果不能，返回如果 DLL 可以卸载，则为 S_OK 或 S_FALSE。  
  
##  <a name="dllgetclassobject"></a>  CAtlDllModuleT::DllGetClassObject  
 返回类工厂。  
  
```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>参数  
 *rclsid*  
 若要创建的对象的 CLSID。  
  
 *riid*  
 所请求的接口的 IID。  
  
 *ppv*  
 通过标识的接口指针的指针*riid*。 如果该对象不支持此接口， *ppv*设置为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain  
 动态链接库 (DLL) 可选入口点。  
  
```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```  
  
### <a name="parameters"></a>参数  
 *dwReason*  
 如果设置为 DLL_PROCESS_ATTACH、 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知调用被禁用。  
  
 *lpreserved，请将*  
 保留。  
  
### <a name="return-value"></a>返回值  
 始终返回 TRUE。  
  
### <a name="remarks"></a>备注  
 禁用 DLL_THREAD_ATTACH 和 dll_thread_detach 发生时通知调用可以进行多线程应用程序具有许多 Dll 的一项实用优化的频繁地创建和删除线程，和是其 Dll 不需要的这些线程级别通知附件/分离。  
  
##  <a name="dllregisterserver"></a>  CAtlDllModuleT::DllRegisterServer  
 将条目添加到系统注册表的 DLL 中的对象。  
  
```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>参数  
 *bRegTypeLib*  
 如果类型库的注册，则为 TRUE。 默认值为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer  
 在 DLL 中的对象在系统注册表中移除项。  
  
```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>参数  
 *bUnRegTypeLib*  
 如果类型库，则若要从注册表中删除，则为 TRUE。 默认值为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
##  <a name="getclassobject"></a>  CAtlDllModuleT::GetClassObject  
 创建指定的 CLSID 的对象。  
  
```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>参数  
 *rclsid*  
 若要创建的对象的 CLSID。  
  
 *riid*  
 所请求的接口的 IID。  
  
 *ppv*  
 通过标识的接口指针的指针*riid*。 如果该对象不支持此接口， *ppv*设置为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 调用此方法[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)是为了向后兼容。  
  
## <a name="see-also"></a>请参阅  
 [CAtlModuleT 类](../../atl/reference/catlmodulet-class.md)   
 [CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)
