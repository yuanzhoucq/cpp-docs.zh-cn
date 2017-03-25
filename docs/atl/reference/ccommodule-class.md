---
title: "CComModule 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
dev_langs:
- C++
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
caps.latest.revision: 23
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d0d5f040d7c6fbe4a4d83da0d589e123588c6bb1
ms.lasthandoff: 03/17/2017

---
# <a name="ccommodule-class"></a>CComModule 类
ATL 7.0 截至`CComModule`不推荐使用︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CComModule : public _ATL_MODULE
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComModule::GetClassObject](#getclassobject)|创建指定的 CLSID 的对象。 对于仅 Dll。|  
|[CComModule::GetModuleInstance](#getmoduleinstance)|返回 `m_hInst`。|  
|[CComModule::GetResourceInstance](#getresourceinstance)|返回 `m_hInstResource`。|  
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|返回 `m_hInstTypeLib`。|  
|[CComModule::Init](#init)|数据成员初始化。|  
|[CComModule::RegisterClassHelper](#registerclasshelper)|在系统注册表中输入对象的标准类注册。|  
|[CComModule::RegisterClassObjects](#registerclassobjects)|注册类对象。 对于仅 Exe。|  
|[CComModule::RegisterServer](#registerserver)|更新在对象映射中的每个对象的系统注册表。|  
|[CComModule::RegisterTypeLib](#registertypelib)|注册类型库。|  
|[CComModule::RevokeClassObjects](#revokeclassobjects)|撤消类对象。 对于仅 Exe。|  
|[CComModule::Term](#term)|释放数据成员。|  
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|从系统注册表中删除对象的标准类注册。|  
|[CComModule::UnregisterServer](#unregisterserver)|注销在对象映射中的每个对象。|  
|[CComModule::UpdateRegistryClass](#updateregistryclass)|注册或注销对象的标准类注册。|  
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|运行指定的资源，若要注册或注销对象中包含的脚本。|  
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|静态链接到 ATL 注册表组件。 运行指定的资源，若要注册或注销对象中包含的脚本。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComModule::m_csObjMap](#m_csobjmap)|确保同步的访问对象的映射信息。|  
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|可确保同步的访问的类型库信息。|  
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|可确保窗口类信息和在窗口创建期间使用的静态数据的同步的访问。|  
|[CComModule::m_hInst](#m_hinst)|包含模块实例的句柄。|  
|[CComModule::m_hInstResource](#m_hinstresource)|默认情况下，包含模块实例的句柄。|  
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|默认情况下，包含模块实例的句柄。|  
|[CComModule::m_pObjMap](#m_pobjmap)|指向由模块实例维护对象映射。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  此类已弃用，和 ATL 代码生成向导现在使用[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)派生的类。 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。 后面的信息可用于与使用 atl。 的较早版本创建的应用程序 `CComModule`仍然是一部分的 ATL 的向后功能。  
  
 `CComModule`实现 COM 服务器模块，从而使客户端来访问该模块的组件。 `CComModule`支持 （进程内） DLL 和 EXE (local) 模块。  
  
 一个`CComModule`实例将使用在对象映射维护一组类对象定义。 此对象映射实现为一个数组`_ATL_OBJMAP_ENTRY`结构，并包含有关的信息︰  
  
-   输入和系统注册表中删除对象说明。  
  
-   通过类工厂的实例化对象。  
  
-   在组件中建立的客户端的根对象之间的通信。  
  
-   执行类对象的生存期管理。  
  
 ATL COM 应用程序向导运行时，向导将自动生成`_Module`的全局实例`CComModule`或从其派生的类。 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
 除了`CComModule`，ATL 还提供[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，用来实现 Exe 和 Windows 服务的单元模型模块。 派生您的模块从`CComAutoThreadModule`如果想要在多个单元中创建对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="getclassobject"></a>CComModule::GetClassObject  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>参数  
 `rclsid`  
 [in]要创建对象的 CLSID。  
  
 `riid`  
 [in]所请求的接口的 IID。  
  
 `ppv`  
 [out]指向由标识的接口指针的指针`riid`。 如果该对象不支持此接口，`ppv`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 创建指定的 CLSID 的对象，并检索到此对象的接口指针。  
  
 `GetClassObject`仅供 Dll。  
  
##  <a name="getmoduleinstance"></a>CComModule::GetModuleInstance  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>返回值  
 `HINSTANCE`识别此模块。  
  
### <a name="remarks"></a>备注  
 返回[m_hInst](#m_hinst)数据成员。  
  
##  <a name="getresourceinstance"></a>CComModule::GetResourceInstance  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>返回值  
 一个 `HINSTANCE`。  
  
### <a name="remarks"></a>备注  
 返回[m_hInstResource](#m_hinstresource)数据成员。  
  
##  <a name="gettypelibinstance"></a>CComModule::GetTypeLibInstance  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HINSTANCE GetTypeLibInstance() const throw();
```  
  
### <a name="return-value"></a>返回值  
 一个 `HINSTANCE`。  
  
### <a name="remarks"></a>备注  
 返回[m_hInstTypeLib](#m_hinsttypelib)数据成员。  
  
##  <a name="init"></a>CComModule::Init  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向对象的映射条目的数组的指针。  
  
 `h`  
 [in]`HINSTANCE`传递给**DLLMain**或`WinMain`。  
  
 `plibid`  
 [in]一个指向与项目关联的类型库的 LIBID。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 所有数据成员都初始化。  
  
##  <a name="m_csobjmap"></a>CComModule::m_csObjMap  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
CRITICAL_SECTION m_csObjMap;
```  
  
### <a name="remarks"></a>备注  
 可确保同步的访问对象映射。  
  
##  <a name="m_cstypeinfoholder"></a>CComModule::m_csTypeInfoHolder  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
CRITICAL_SECTION m_csTypeInfoHolder;
```  
  
### <a name="remarks"></a>备注  
 可确保对该类型库的同步的访问。  
  
##  <a name="m_cswindowcreate"></a>CComModule::m_csWindowCreate  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
CRITICAL_SECTION m_csWindowCreate;
```  
  
### <a name="remarks"></a>备注  
 可确保窗口类信息并在窗口创建期间使用的静态数据的同步的访问。  
  
##  <a name="m_hinst"></a>CComModule::m_hInst  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HINSTANCE m_hInst;
```  
  
### <a name="remarks"></a>备注  
 包含模块实例的句柄。  
  
 [Init](#init)方法设置`m_hInst`到句柄传递给**DLLMain**或`WinMain`。  
  
##  <a name="m_hinstresource"></a>CComModule::m_hInstResource  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HINSTANCE m_hInstResource;
```  
  
### <a name="remarks"></a>备注  
 默认情况下，包含模块实例的句柄。  
  
 [Init](#init)方法设置`m_hInstResource`到句柄传递给**DLLMain**或`WinMain`。 您可以明确设置`m_hInstResource`资源的句柄。  
  
 [GetResourceInstance](#getresourceinstance)方法返回的句柄存储在`m_hInstResource`。  
  
##  <a name="m_hinsttypelib"></a>CComModule::m_hInstTypeLib  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HINSTANCE m_hInstTypeLib;
```  
  
### <a name="remarks"></a>备注  
 默认情况下，包含模块实例的句柄。  
  
 [Init](#init)方法设置`m_hInstTypeLib`到句柄传递给**DLLMain**或`WinMain`。 您可以明确设置`m_hInstTypeLib`类型库的句柄。  
  
 [GetTypeLibInstance](#gettypelibinstance)方法返回的句柄存储在`m_hInstTypeLib`。  
  
##  <a name="m_pobjmap"></a>CComModule::m_pObjMap  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```  
  
### <a name="remarks"></a>备注  
 指向由模块实例维护对象映射。  
  
##  <a name="registerclasshelper"></a>CComModule::RegisterClassHelper  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
ATL_DEPRECATED HRESULT RegisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 [in]要注册该对象的 CLSID。  
  
 `lpszProgID`  
 [in]与此对象的 ProgID。  
  
 `lpszVerIndProgID`  
 [in]与对象相关联版本无关的 ProgID。  
  
 `nDescID`  
 [in]对象的说明的字符串资源的标识符。  
  
 `dwFlags`  
 [in]指定要在注册表中输入的线程模型。 可能的值为**THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 在系统注册表中输入对象的标准类注册。  
  
 [UpdateRegistryClass](#updateregistryclass)方法调用`RegisterClassHelper`。  
  
##  <a name="registerclassobjects"></a>CComModule::RegisterClassObjects  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwClsContext`  
 [in]指定的类对象将在其中运行的上下文。 可能的值为**CLSCTX_INPROC_SERVER**， **CLSCTX_INPROC_HANDLER**，或**CLSCTX_LOCAL_SERVER**。 有关这些值的说明，请参阅[CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwFlags`  
 [in]确定对类对象的连接类型。 可能的值为**REGCLS_SINGLEUSE**， **REGCLS_MULTIPLEUSE**，或**REGCLS_MULTI_SEPARATE**。 有关这些值的说明，请参阅[结合指定](http://msdn.microsoft.com/library/windows/desktop/ms679697)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 向 OLE 注册 EXE 类对象，以便其他应用程序可以连接到它。 此方法仅供 Exe。  
  
##  <a name="registerserver"></a>CComModule::RegisterServer  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 `bRegTypeLib`  
 [in]指示是否将已注册类型库。 默认值是**FALSE**。  
  
 `pCLSID`  
 [in]指向要注册的对象的 CLSID。 如果**NULL** （默认值），将注册在对象映射中的所有对象。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 具体取决于`pCLSID`参数，将更新系统注册表的单个类对象或者在对象映射中的所有对象。  
  
 如果`bRegTypeLib`是**TRUE**，类型库信息也将进行更新。  
  
 请参阅[OBJECT_ENTRY_AUTO](http://msdn.microsoft.com/library/5a0f4fa5-0905-43d2-b337-e22f979c9e4c)有关如何向对象映射中添加项的信息。  
  
 `RegisterServer`将自动调用**DLLRegisterServer**的 DLL 或`WinMain`为使用运行 EXE **/RegServer**命令行选项。  
  
##  <a name="registertypelib"></a>CComModule::RegisterTypeLib  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszIndex`  
 [in]格式字符串`"\\N"`，其中`N`整数索引的类型库资源。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 将类型库的信息添加到系统注册表。  
  
 如果模块实例中包含多个类型库，使用此方法的第二个版本可指定应使用哪些类型库。  
  
##  <a name="revokeclassobjects"></a>CComModule::RevokeClassObjects  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 删除类的对象。 此方法仅供 Exe。  
  
##  <a name="term"></a>CComModule::Term  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>备注  
 释放所有数据成员。  
  
##  <a name="unregisterclasshelper"></a>CComModule::UnregisterClassHelper  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 [in]要取消注册该对象的 CLSID。  
  
 `lpszProgID`  
 [in]与此对象的 ProgID。  
  
 `lpszVerIndProgID`  
 [in]与对象相关联版本无关的 ProgID。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 从系统注册表中删除对象的标准类注册。  
  
 [UpdateRegistryClass](#updateregistryclass)方法调用`UnregisterClassHelper`。  
  
##  <a name="unregisterserver"></a>CComModule::UnregisterServer  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```  
  
### <a name="parameters"></a>参数  
 `bUnRegTypeLib`  
 如果**TRUE**，类型库也是未注册。  
  
 `pCLSID`  
 指向要取消注册的对象的 CLSID。 如果**NULL** （默认值），在对象映射中的所有对象将都被注销。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 具体取决于`pCLSID`参数，注销的类单一对象或对象映射中的所有对象。  
  
 `UnregisterServer`将自动调用**DLLUnregisterServer**的 DLL 或`WinMain`为使用运行 EXE **/UnregServer**命令行选项。  
  
 请参阅[OBJECT_ENTRY_AUTO](http://msdn.microsoft.com/library/5a0f4fa5-0905-43d2-b337-e22f979c9e4c)有关如何向对象映射中添加项的信息。  
  
##  <a name="updateregistryclass"></a>CComModule::UpdateRegistryClass  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
ATL_DEPRECATED HRESULT UpdateRegistryClass(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 要注册或注销了该对象的 CLSID。  
  
 `lpszProgID`  
 与此对象的 ProgID。  
  
 `lpszVerIndProgID`  
 与对象相关联版本无关的 ProgID。  
  
 `nDescID`  
 对象的说明的字符串资源的标识符。  
  
 `szDesc`  
 包含对象的说明的字符串。  
  
 `dwFlags`  
 指定要在注册表中输入的线程模型。 可能的值为**THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
 `bRegister`  
 指示是否应注册该对象。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果`bRegister`是**TRUE**，此方法将在系统注册表中输入对象的标准类注册。  
  
 如果`bRegister`是**FALSE**，它会删除该对象的注册。  
  
 具体取决于值`bRegister`，`UpdateRegistryClass`调用[RegisterClassHelper](#registerclasshelper)或[UnregisterClassHelper](#unregisterclasshelper)。  
  
 通过指定[DECLARE_REGISTRY](http://msdn.microsoft.com/library/89b8949b-5c27-4a9c-8a51-ad276bba3a54)宏，`UpdateRegistryClass`处理您的对象图时将自动调用。  
  
##  <a name="updateregistryfromresourced"></a>CComModule::UpdateRegistryFromResourceD  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
virtual HRESULT UpdateRegistryFromResourceD(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```  
  
### <a name="parameters"></a>参数  
 `lpszRes`  
 [in]资源名称。  
  
 `nResID`  
 [in]资源 id。  
  
 `bRegister`  
 [in]指示是否应注册该对象。  
  
 `pMapEntries`  
 [in]指向替换映射存储相关联的脚本可替换参数的值的指针。 会自动使用 ATL `%MODULE%`。 若要使用其他可替换参数，请参阅有关的详细信息备注。 否则，请使用**NULL**默认值。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 运行指定的资源中包含的脚本`lpszRes`或`nResID`。  
  
 如果`bRegister`是**TRUE**，此方法在系统注册表中注册该对象; 否则，它中注销的对象。  
  
 通过指定[DECLARE_REGISTRY_RESOURCE](http://msdn.microsoft.com/library/7ac11498-8ee2-4156-8df2-7076f7ddda8b)或[DECLARE_REGISTRY_RESOURCEID](http://msdn.microsoft.com/library/65bf3576-5396-416e-ba48-e14b3236c49b)宏，`UpdateRegistryFromResourceD`处理您的对象图时将自动调用。  
  
> [!NOTE]
>  若要在运行时替换的替换值，不指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`宏。 相反，创建一个数组**_ATL_REGMAP_ENTRIES**结构，其中每个条目都包含一个变量占位符与一个要在运行时替换占位符值成对出现。 然后，调用`UpdateRegistryFromResourceD`，将数组传递`pMapEntries`参数。 这会将添加中的所有替换值**_ATL_REGMAP_ENTRIES**到注册机构的替换映射的结构。  
  
> [!NOTE]
>  若要静态链接到 ATL 注册表组件 （注册器），请参阅[UpdateRegistryFromResourceS](#updateregistryfromresources)。  
  
 有关可替换参数和脚本的详细信息，请参阅文章[ATL 注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)。  
  
##  <a name="updateregistryfromresources"></a>CComModule::UpdateRegistryFromResourceS  
 ATL 7.0 截至`CComModule`已过时︰ 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
```
virtual HRESULT UpdateRegistryFromResourceS(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszRes`  
 [in]资源名称。  
  
 `nResID`  
 [in]资源 id。  
  
 `bRegister`  
 [in]指示是否应注册为资源脚本。  
  
 `pMapEntries`  
 [in]指向替换映射存储相关联的脚本可替换参数的值的指针。 会自动使用 ATL `%MODULE%`。 若要使用其他可替换参数，请参阅有关的详细信息备注。 否则，请使用**NULL**默认值。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 类似于[UpdateRegistryFromResourceD](#updateregistryfromresourced)除`UpdateRegistryFromResourceS`创建静态链接到 ATL 注册表组件 （注册器）。  
  
 `UpdateRegistryFromResourceS`将调用自动处理对象映射时，提供您添加`#define _ATL_STATIC_REGISTRY`到您 stdafx.h。  
  
> [!NOTE]
>  若要在运行时替换的替换值，不指定[DECLARE_REGISTRY_RESOURCE](http://msdn.microsoft.com/library/7ac11498-8ee2-4156-8df2-7076f7ddda8b)或[DECLARE_REGISTRY_RESOURCEID](http://msdn.microsoft.com/library/65bf3576-5396-416e-ba48-e14b3236c49b)宏。 相反，创建一个数组**_ATL_REGMAP_ENTRIES**结构，其中每个条目都包含一个变量占位符与一个要在运行时替换占位符值成对出现。 然后，调用`UpdateRegistryFromResourceS`，将数组传递`pMapEntries`参数。 这会将添加中的所有替换值**_ATL_REGMAP_ENTRIES**到注册机构的替换映射的结构。  
  
 有关可替换参数和脚本的详细信息，请参阅文章[ATL 注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

