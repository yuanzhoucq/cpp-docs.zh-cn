---
title: CComModule 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: 53138081a6d712f775a2cc8f1e6905c45d95d34d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497110"
---
# <a name="ccommodule-class"></a>CComModule 类

在 atl 7.0 中, `CComModule`已弃用: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|创建指定 CLSID 的对象。 仅适用于 Dll。|
|[CComModule::GetModuleInstance](#getmoduleinstance)|返回 `m_hInst`。|
|[CComModule::GetResourceInstance](#getresourceinstance)|返回 `m_hInstResource`。|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|返回 `m_hInstTypeLib`。|
|[CComModule::Init](#init)|初始化数据成员。|
|[CComModule::RegisterClassHelper](#registerclasshelper)|在系统注册表中输入对象的标准类注册。|
|[CComModule::RegisterClassObjects](#registerclassobjects)|注册类对象。 仅适用于 Exe。|
|[CComModule::RegisterServer](#registerserver)|为对象映射中的每个对象更新系统注册表。|
|[CComModule::RegisterTypeLib](#registertypelib)|注册类型库。|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|撤消类对象。 仅适用于 Exe。|
|[CComModule::Term](#term)|释放数据成员。|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|从系统注册表中移除对象的标准类注册。|
|[CComModule::UnregisterServer](#unregisterserver)|在对象映射中注销每个对象。|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|注册或取消注册对象的标准类注册。|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|运行指定资源中包含的脚本, 以注册或取消注册对象。|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|指向 ATL 注册表组件的静态链接。 运行指定资源中包含的脚本, 以注册或取消注册对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|确保对对象映射信息的同步访问。|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|确保对类型库信息的同步访问。|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|确保对窗口类信息和在窗口创建期间使用的静态数据的同步访问。|
|[CComModule::m_hInst](#m_hinst)|包含模块实例的句柄。|
|[CComModule::m_hInstResource](#m_hinstresource)|默认情况下, 包含模块实例的句柄。|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|默认情况下, 包含模块实例的句柄。|
|[CComModule::m_pObjMap](#m_pobjmap)|指向模块实例维护的对象映射。|

## <a name="remarks"></a>备注

> [!NOTE]
>  此类已弃用, 并且 ATL 代码生成向导现在使用[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)派生类。 有关详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。 下面的信息适用于使用较旧版本的 ATL 创建的应用程序。 `CComModule`仍是 ATL 的一部分, 用于向后功能。

`CComModule`实现一个 COM 服务器模块, 使客户端能够访问该模块的组件。 `CComModule`支持 DLL (进程内) 和 EXE (本地) 模块。

`CComModule`实例使用对象映射来维护一组类对象定义。 此对象映射作为`_ATL_OBJMAP_ENTRY`结构数组实现, 并包含以下内容的信息:

- 在系统注册表中输入和删除对象说明。

- 通过类工厂实例化对象。

- 在组件中建立客户端和根对象之间的通信。

- 执行类对象的生存期管理。

运行 ATL COM 运行向导时, 向导会自动生成`_Module`, `CComModule`或从其派生的类的全局实例。 有关 ATL 项目向导的详细信息, 请参阅文章[创建 Atl 项目](../../atl/reference/creating-an-atl-project.md)。

除外`CComModule`, ATL 还提供[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), 它为 exe 和 Windows 服务实现了单元模型模块。 如果要在多`CComAutoThreadModule`个单元中创建对象, 请从派生模块。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>要求

**标头:** atlbase。h

##  <a name="getclassobject"></a>CComModule:: GetClassObject

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>参数

*rclsid*<br/>
中要创建的对象的 CLSID。

*riid*<br/>
中所请求的接口的 IID。

*ppv*<br/>
弄指向由*riid*标识的接口指针的指针。 如果对象不支持此接口, 则将*ppv*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

创建指定 CLSID 的对象, 并检索此对象的接口指针。

`GetClassObject`仅适用于 Dll。

##  <a name="getmoduleinstance"></a>CComModule:: GetModuleInstance

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>返回值

标识此模块的 HINSTANCE。

### <a name="remarks"></a>备注

返回[m_hInst](#m_hinst)数据成员。

##  <a name="getresourceinstance"></a>CComModule:: GetResourceInstance

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>返回值

一个 HINSTANCE。

### <a name="remarks"></a>备注

返回[m_hInstResource](#m_hinstresource)数据成员。

##  <a name="gettypelibinstance"></a>CComModule:: GetTypeLibInstance

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>返回值

一个 HINSTANCE。

### <a name="remarks"></a>备注

返回[m_hInstTypeLib](#m_hinsttypelib)数据成员。

##  <a name="init"></a>CComModule:: Init

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
中指向对象映射项的数组的指针。

*h*<br/>
中传递给`DLLMain`或`WinMain`的 HINSTANCE。

*plibid*<br/>
中一个指针, 指向与项目关联的类型库的 LIBID。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

初始化所有数据成员。

##  <a name="m_csobjmap"></a>CComModule:: m_csObjMap

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>备注

确保对对象映射的同步访问。

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>备注

确保对类型库的同步访问。

##  <a name="m_cswindowcreate"></a>CComModule:: m_csWindowCreate

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>备注

确保对窗口类信息和创建窗口期间使用的静态数据的同步访问。

##  <a name="m_hinst"></a>CComModule:: m_hInst

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>备注

包含模块实例的句柄。

[Init](#init)方法将设置`m_hInst`为传递给`DLLMain`或`WinMain`的句柄。

##  <a name="m_hinstresource"></a>CComModule:: m_hInstResource

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>备注

默认情况下, 包含模块实例的句柄。

[Init](#init)方法将设置`m_hInstResource`为传递给`DLLMain`或`WinMain`的句柄。 可以显式设置`m_hInstResource`为资源的句柄。

[GetResourceInstance](#getresourceinstance)方法返回存储在中`m_hInstResource`的句柄。

##  <a name="m_hinsttypelib"></a>CComModule:: m_hInstTypeLib

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>备注

默认情况下, 包含模块实例的句柄。

[Init](#init)方法将设置`m_hInstTypeLib`为传递给`DLLMain`或`WinMain`的句柄。 您可以显式设置`m_hInstTypeLib`为类型库的句柄。

[GetTypeLibInstance](#gettypelibinstance)方法返回存储在中`m_hInstTypeLib`的句柄。

##  <a name="m_pobjmap"></a>CComModule:: m_pObjMap

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>备注

指向模块实例维护的对象映射。

##  <a name="registerclasshelper"></a>CComModule:: RegisterClassHelper

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>参数

*clsid*<br/>
中要注册的对象的 CLSID。

*lpszProgID*<br/>
中与对象关联的 ProgID。

*lpszVerIndProgID*<br/>
中与对象关联的独立于版本的 ProgID。

*nDescID*<br/>
中对象的说明的字符串资源的标识符。

*dwFlags*<br/>
中指定要在注册表中输入的线程模型。 可能的值包括 THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

在系统注册表中输入对象的标准类注册。

[UpdateRegistryClass](#updateregistryclass)方法将调用`RegisterClassHelper`。

##  <a name="registerclassobjects"></a>CComModule:: RegisterClassObjects

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>参数

*dwClsContext*<br/>
中指定要在其中运行类对象的上下文。 可能的值包括 CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。 有关这些值的说明, 请参阅 Windows SDK 中的[CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) 。

*dwFlags*<br/>
中确定类对象的连接类型。 可能的值包括 REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。 有关这些值的说明, 请参阅 Windows SDK 中的[REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) 。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

向 OLE 注册 EXE 类对象, 以便其他应用程序可以连接到它。 此方法仅适用于 Exe。

##  <a name="registerserver"></a>CComModule:: RegisterServer

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>参数

*bRegTypeLib*<br/>
中指示是否将注册类型库。 默认值是 FALSE。

*pCLSID*<br/>
中指向要注册的对象的 CLSID。 如果为 NULL (默认值), 则将注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

根据*pCLSID*参数, 为对象映射中的单个类对象或所有对象更新系统注册表。

如果*bRegTypeLib*为 TRUE, 则还会更新类型库信息。

请参阅[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) , 以获取有关如何将条目添加到对象映射的信息。

`RegisterServer``DLLRegisterServer`对于 DLL, `WinMain`或对于使用`/RegServer`命令行选项运行的 EXE, 将自动调用。

##  <a name="registertypelib"></a>CComModule:: RegisterTypeLib

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>参数

*lpszIndex*<br/>
中格式`"\\N"`的字符串, 其中`N`是 TYPELIB 资源的整数索引。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

将有关类型库的信息添加到系统注册表中。

如果模块实例包含多个类型库, 请使用此方法的第二个版本来指定应使用的类型库。

##  <a name="revokeclassobjects"></a>CComModule:: RevokeClassObjects

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

删除类对象。 此方法仅适用于 Exe。

##  <a name="term"></a>CComModule:: Term

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
void Term() throw();
```

### <a name="remarks"></a>备注

释放所有数据成员。

##  <a name="unregisterclasshelper"></a>CComModule:: UnregisterClassHelper

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>参数

*clsid*<br/>
中要注销的对象的 CLSID。

*lpszProgID*<br/>
中与对象关联的 ProgID。

*lpszVerIndProgID*<br/>
中与对象关联的独立于版本的 ProgID。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

从系统注册表中移除对象的标准类注册。

[UpdateRegistryClass](#updateregistryclass)方法将调用`UnregisterClassHelper`。

##  <a name="unregisterserver"></a>CComModule:: UnregisterServer

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>参数

*bUnRegTypeLib*<br/>
如果为 TRUE, 则也取消注册类型库。

*pCLSID*<br/>
指向要注销的对象的 CLSID。 如果为 NULL (默认值), 则将取消注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

根据*pCLSID*参数, 取消注册单个类对象或对象映射中的所有对象。

`UnregisterServer``DLLUnregisterServer`对于 DLL, `WinMain`或对于使用`/UnregServer`命令行选项运行的 EXE, 将自动调用。

请参阅[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) , 以获取有关如何将条目添加到对象映射的信息。

##  <a name="updateregistryclass"></a>CComModule:: UpdateRegistryClass

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

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

*clsid*<br/>
要注册或取消注册的对象的 CLSID。

*lpszProgID*<br/>
与对象关联的 ProgID。

*lpszVerIndProgID*<br/>
与对象关联的独立于版本的 ProgID。

*nDescID*<br/>
对象的说明的字符串资源的标识符。

*szDesc*<br/>
一个包含对象说明的字符串。

*dwFlags*<br/>
指定要在注册表中输入的线程模型。 可能的值包括 THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

*bRegister*<br/>
指示是否应注册对象。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果*bRegister*为 TRUE, 则此方法将在系统注册表中输入对象的标准类注册。

如果*bRegister*为 FALSE, 则删除对象的注册。

根据*bRegister*的值, `UpdateRegistryClass`调用[RegisterClassHelper](#registerclasshelper)或[UnregisterClassHelper](#unregisterclasshelper)。

通过指定[DECLARE_REGISTRY](registry-macros.md#declare_registry)宏, `UpdateRegistryClass`处理对象映射时将自动调用。

##  <a name="updateregistryfromresourced"></a>CComModule:: UpdateRegistryFromResourceD

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

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

*lpszRes*<br/>
中资源名称。

*nResID*<br/>
中资源 ID。

*bRegister*<br/>
中指示是否应注册对象。

*pMapEntries*<br/>
中指向替换映射的指针, 该指针存储与脚本的可替换参数关联的值。 ATL 自动使用`%MODULE%`。 若要使用其他可替换的参数, 请参阅备注获取详细信息。 否则, 请使用 NULL 默认值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

运行*lpszRes*或*nResID*指定的资源中包含的脚本。

如果*bRegister*为 TRUE, 则此方法将在系统注册表中注册对象;否则, 将取消注册对象。

通过指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)宏, `UpdateRegistryFromResourceD`在处理对象映射时将自动调用。

> [!NOTE]
>  若要在运行时替换替换值, 请不要指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 宏。 而是创建结构的`_ATL_REGMAP_ENTRIES`数组, 其中每个条目都包含一个与值配对的变量占位符, 以便在运行时替换占位符。 然后调用`UpdateRegistryFromResourceD`, 传递*pMapEntries*参数的数组。 这会将`_ATL_REGMAP_ENTRIES`结构中的所有替换值添加到注册机构的替换地图。

> [!NOTE]
>  若要以静态方式链接到 ATL 注册表组件 (注册器), 请参阅[UpdateRegistryFromResourceS](#updateregistryfromresources)。

有关可替换参数和脚本的详细信息, 请参阅[ATL 注册表组件 (注册器)](../../atl/atl-registry-component-registrar.md)一文。

##  <a name="updateregistryfromresources"></a>CComModule:: UpdateRegistryFromResourceS

在 atl 7.0 中, `CComModule`已过时: 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

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

*lpszRes*<br/>
中资源名称。

*nResID*<br/>
中资源 ID。

*bRegister*<br/>
中指示是否应注册资源脚本。

*pMapEntries*<br/>
中指向替换映射的指针, 该指针存储与脚本的可替换参数关联的值。 ATL 自动使用`%MODULE%`。 若要使用其他可替换的参数, 请参阅备注获取详细信息。 否则, 请使用 NULL 默认值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

类似于[UpdateRegistryFromResourceD](#updateregistryfromresourced) , `UpdateRegistryFromResourceS`但会创建指向 ATL 注册表组件 (注册器) 的静态链接。

`UpdateRegistryFromResourceS`当你将对象映射添加`#define _ATL_STATIC_REGISTRY`到 stdafx.h 时, 将自动调用。

> [!NOTE]
>  若要在运行时替换替换值, 请不要指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)宏。 而是创建结构的`_ATL_REGMAP_ENTRIES`数组, 其中每个条目都包含一个与值配对的变量占位符, 以便在运行时替换占位符。 然后调用`UpdateRegistryFromResourceS`, 传递*pMapEntries*参数的数组。 这会将`_ATL_REGMAP_ENTRIES`结构中的所有替换值添加到注册机构的替换地图。

有关可替换参数和脚本的详细信息, 请参阅[ATL 注册表组件 (注册器)](../../atl/atl-registry-component-registrar.md)一文。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
