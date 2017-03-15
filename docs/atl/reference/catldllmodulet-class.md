---
title: "CAtlDllModuleT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAtlDllModuleT
- ATL::CAtlDllModuleT<T>
- ATL::CAtlDllModuleT
- ATL.CAtlDllModuleT<T>
- CAtlDllModuleT
dev_langs:
- C++
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 13cd0adb860660e06c92e8f02c07721ede391fb7
ms.lasthandoff: 02/24/2017

---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT 类
此类表示对 DLL 的模块。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类派生自`CAtlDllModuleT`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|构造函数。|  
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|测试是否可以卸载 DLL。|  
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|返回类工厂。|  
|[CAtlDllModuleT::DllMain](#dllmain)|动态链接库 (DLL) 可选入口点。|  
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|将条目添加到系统注册表中的 DLL 中的对象。|  
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|在系统注册表中的 DLL 中的对象中移除项。|  
|[CAtlDllModuleT::GetClassObject](#getclassobject)|返回类工厂。 通过调用[DllGetClassObject](#dllgetclassobject)。|  
  
## <a name="remarks"></a>备注  
 `CAtlDllModuleT`表示一个动态链接库 (DLL) 的模块并提供使用 DLL 的所有项目的函数。 此专用化[CAtlModuleT](../../atl/reference/catlmodulet-class.md)类包括支持以进行注册。  
  
 ATL 中的模块的详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="a-namecatldllmoduleta--catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT  
 构造函数。  
  
```
CAtlDllModuleT() throw();
```  
  
##  <a name="a-namedtora--catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModuleT:: ~ CAtlDllModuleT  
 析构函数。  
  
```
~CAtlDllModuleT() throw();
```  
  
##  <a name="a-namedllcanunloadnowa--catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow  
 测试是否可以卸载 DLL。  
  
```
HRESULT DllCanUnloadNow() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果不能，返回 S_OK，如果该 DLL 可以被卸载或 S_FALSE。  
  
##  <a name="a-namedllgetclassobjecta--catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject  
 返回类工厂。  
  
```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>参数  
 `rclsid`  
 要创建对象的 CLSID。  
  
 `riid`  
 所请求的接口的 IID。  
  
 `ppv`  
 指向由标识的接口指针的指针`riid`。 如果该对象不支持此接口，`ppv`设置为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="a-namedllmaina--catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::DllMain  
 动态链接库 (DLL) 可选入口点。  
  
```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwReason`  
 如果设置为 DLL_PROCESS_ATTACH、 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知调用处于禁用状态。  
  
 *lpReserved*  
 保留。  
  
### <a name="return-value"></a>返回值  
 始终返回 TRUE。  
  
### <a name="remarks"></a>备注  
 禁用 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知调用可以是具有多个 Dll，频繁地创建和删除线程，并且其 Dll 不需要附件/分离这些线程级通知的多线程应用程序优化的有用。  
  
##  <a name="a-namedllregisterservera--catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer  
 将条目添加到系统注册表中的 DLL 中的对象。  
  
```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>参数  
 `bRegTypeLib`  
 如果要注册类型库，则为 TRUE。 默认值为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="a-namedllunregisterservera--catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer  
 在系统注册表中的 DLL 中的对象中移除项。  
  
```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>参数  
 `bUnRegTypeLib`  
 如果类型库是从注册表中删除，则为 TRUE。 默认值为 TRUE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="a-namegetclassobjecta--catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT::GetClassObject  
 创建指定的 CLSID 的对象。  
  
```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>参数  
 `rclsid`  
 要创建对象的 CLSID。  
  
 `riid`  
 所请求的接口的 IID。  
  
 `ppv`  
 指向由标识的接口指针的指针`riid`。 如果该对象不支持此接口，`ppv`设置为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 此方法由[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)和包含是为了向后兼容性。  
  
## <a name="see-also"></a>另请参阅  
 [CAtlModuleT 类](../../atl/reference/catlmodulet-class.md)   
 [CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)

