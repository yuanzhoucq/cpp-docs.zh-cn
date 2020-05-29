---
title: CComModule 类
ms.date: 08/19/2019
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
ms.openlocfilehash: 5e30f847ff99a80ab19b880728472a339fd4cbe5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747925"
---
# <a name="ccommodule-class"></a>CComModule 类

自 ATL 7.0`CComModule`起，已弃用：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom 模块：获取类对象](#getclassobject)|创建指定 CLSID 的对象。 仅适用于 DLL。|
|[CCom 模块：获取模块实例](#getmoduleinstance)|返回 `m_hInst`。|
|[CCom 模块：获取资源实例](#getresourceinstance)|返回 `m_hInstResource`。|
|[CCom 模块：获取类型 Lib实例](#gettypelibinstance)|返回 `m_hInstTypeLib`。|
|[CCom模块：：Init](#init)|初始化数据成员。|
|[CCom模块：：注册类帮助者](#registerclasshelper)|在系统注册表中输入对象的标准类注册。|
|[CCom 模块：：注册类对象](#registerclassobjects)|注册类对象。 仅适用于 EXEs。|
|[CCom 模块：：注册服务器](#registerserver)|更新对象映射中每个对象的系统注册表。|
|[CCom模块：：注册类型Lib](#registertypelib)|注册类型库。|
|[CCom 模块：：撤销类对象](#revokeclassobjects)|撤消类对象。 仅适用于 EXEs。|
|[CCom 模块：：学期](#term)|释放数据成员。|
|[CCom 模块：：未注册类帮助程序](#unregisterclasshelper)|从系统注册表中删除对象的标准类注册。|
|[CCom 模块：：取消注册服务器](#unregisterserver)|取消注册对象映射中的每个对象。|
|[CCom 模块：：更新注册表类](#updateregistryclass)|注册或取消注册对象的标准类注册。|
|[CCom 模块：：从资源中更新注册表](#updateregistryfromresourced)|运行指定资源中包含的脚本以注册或取消注册对象。|
|[CCom模块：：从资源更新注册表](#updateregistryfromresources)|静态链接到 ATL 注册表组件。 运行指定资源中包含的脚本以注册或取消注册对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCom模块：m_csObjMap](#m_csobjmap)|确保同步访问对象映射信息。|
|[CCom模块：：m_csTypeInfoHolder](#m_cstypeinfoholder)|确保同步访问类型库信息。|
|[CCom模块：m_csWindowCreate](#m_cswindowcreate)|确保同步访问窗口创建期间使用的窗口类信息和静态数据。|
|[CCom模块：：m_hInst](#m_hinst)|包含模块实例的句柄。|
|[CCom模块：m_hInstResource](#m_hinstresource)|默认情况下，包含模块实例的句柄。|
|[CCom模块：：m_hInstTypeLib](#m_hinsttypelib)|默认情况下，包含模块实例的句柄。|
|[CCom模块：m_pObjMap](#m_pobjmap)|指向模块实例维护的对象映射。|

## <a name="remarks"></a>备注

> [!NOTE]
> 此类被弃用，ATL 代码生成向导现在使用[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)派生类。 有关详细信息[，请参阅 ATL 模块课程](../../atl/atl-module-classes.md)。 以下信息适用于使用旧版本的 ATL 创建的应用程序。 `CComModule`仍然是 ATL 的一部分，用于向后功能。

`CComModule`实现 COM 服务器模块，允许客户端访问模块的组件。 `CComModule`支持 DLL（在位）和 EXE（本地）模块。

实例`CComModule`使用对象映射来维护一组类对象定义。 此对象映射作为结构数组`_ATL_OBJMAP_ENTRY`实现，并包含用于：

- 在系统注册表中输入和删除对象描述。

- 通过类工厂实例化对象。

- 建立客户端和组件中的根对象之间的通信。

- 执行类对象的生存期管理。

运行 ATL COM 应用向导时，向导会自动生成`_Module`的`CComModule`全局实例或派生自它的类。 有关 ATL 项目向导的详细信息，请参阅创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)的文章。

此外，ATL`CComModule`还提供[CComAutoThread 模块](../../atl/reference/ccomautothreadmodule-class.md)，该模块为 EXEs 和 Windows 服务实现了单元模型模块。 从`CComAutoThreadModule`要在多个单元中创建对象时派生模块。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a>CCom 模块：获取类对象

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>参数

*rclsid*<br/>
[在]要创建的对象的 CLSID。

*riid*<br/>
[在]请求接口的 IID。

*Ppv*<br/>
[出]指向*riid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppv*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

创建指定的 CLSID 的对象并检索指向此对象的接口指针。

`GetClassObject`仅适用于 DLL。

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CCom 模块：获取模块实例

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>返回值

识别此模块的 HINSTANCE。

### <a name="remarks"></a>备注

返回[m_hInst](#m_hinst)数据成员。

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a>CCom 模块：获取资源实例

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>返回值

一个哈普。

### <a name="remarks"></a>备注

返回[m_hInstResource](#m_hinstresource)数据成员。

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a>CCom 模块：获取类型 Lib实例

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>返回值

一个哈普。

### <a name="remarks"></a>备注

返回[m_hInstTypeLib](#m_hinsttypelib)数据成员。

## <a name="ccommoduleinit"></a><a name="init"></a>CCom模块：：Init

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向对象映射条目数组的指针。

*H*<br/>
[在]传递给`DLLMain`或`WinMain`的 HINSTANCE。

*普利比德*<br/>
[在]指向与项目关联的类型库的 LIBID 的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

初始化所有数据成员。

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a>CCom模块：m_csObjMap

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>备注

确保同步访问对象映射。

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a>CCom模块：：m_csTypeInfoHolder

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>备注

确保同步访问类型库。

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a>CCom模块：m_csWindowCreate

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>备注

确保同步访问窗口类信息和窗口创建期间使用的静态数据。

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a>CCom模块：：m_hInst

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>备注

包含模块实例的句柄。

[Init](#init)方法集`m_hInst`到传递给`DLLMain`或`WinMain`的句柄。

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a>CCom模块：m_hInstResource

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>备注

默认情况下，包含模块实例的句柄。

[Init](#init)方法集`m_hInstResource`到传递给`DLLMain`或`WinMain`的句柄。 您可以显式设置为`m_hInstResource`资源的句柄。

[GetResourceInstance](#getresourceinstance)方法返回存储在 中的`m_hInstResource`句柄。

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a>CCom模块：：m_hInstTypeLib

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>备注

默认情况下，包含模块实例的句柄。

[Init](#init)方法集`m_hInstTypeLib`到传递给`DLLMain`或`WinMain`的句柄。 您可以显式设置为`m_hInstTypeLib`类型库的句柄。

[GetTypeLibinstance](#gettypelibinstance)方法返回存储在 中的`m_hInstTypeLib`句柄。

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a>CCom模块：m_pObjMap

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>备注

指向模块实例维护的对象映射。

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a>CCom模块：：注册类帮助者

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>参数

*Clsid*<br/>
[在]要注册的对象的 CLSID。

*lpszProgID*<br/>
[在]与对象关联的 ProgID。

*lpszVerindProgID*<br/>
[在]与对象关联的版本无关的 ProgID。

*nDescID*<br/>
[在]对象描述的字符串资源的标识符。

dwFlags**<br/>
[在]指定要在注册表中输入的线程模型。 可能的值是THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

在系统注册表中输入对象的标准类注册。

[更新注册表类](#updateregistryclass)方法调用`RegisterClassHelper`。

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a>CCom 模块：：注册类对象

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>参数

*dwCls上下文*<br/>
[在]指定要在其中运行类对象的上下文。 可能的值是CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER或CLSCTX_LOCAL_SERVER。 有关这些值的说明，请参阅 Windows SDK 中的[CLSCTX。](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx)

dwFlags**<br/>
[在]确定与类对象的连接类型。 可能的值是REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或REGCLS_MULTI_SEPARATE。 有关这些值的说明，请参阅 Windows SDK 中的[REGCLS。](/windows/win32/api/combaseapi/ne-combaseapi-regcls)

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

将 EXE 类对象注册到 OLE，以便其他应用程序可以连接到它。 此方法仅适用于 EXEs。

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a>CCom 模块：：注册服务器

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>参数

*bRegTypeLib*<br/>
[在]指示类型库是否将注册。 默认值是 FALSE。

*pCLSID*<br/>
[在]指向要注册的对象的 CLSID。 如果 NULL（默认值），则将注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

根据*pCLSID*参数，更新单个类对象或对象映射中的所有对象的系统注册表。

如果*bRegTypeLib*为 TRUE，则类型库信息也将更新。

有关如何向对象映射添加条目的信息，请参阅[OBJECT_ENTRY_AUTO。](object-map-macros.md#object_entry_auto)

`RegisterServer`将自动调用`DLLRegisterServer`DLL 或使用`WinMain`命令行选项运行的`/RegServer`EXE。

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a>CCom模块：：注册类型Lib

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>参数

*lpszIndex*<br/>
[在]格式`"\\N"`的字符串 ，`N`其中是 TYPELIB 资源的整数索引。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

将有关类型库的信息添加到系统注册表。

如果模块实例包含多个类型库，请使用此方法的第二个版本指定应使用的类型库。

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a>CCom 模块：：撤销类对象

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

删除类对象。 此方法仅适用于 EXEs。

## <a name="ccommoduleterm"></a><a name="term"></a>CCom 模块：：学期

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```cpp
void Term() throw();
```

### <a name="remarks"></a>备注

释放所有数据成员。

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a>CCom 模块：：未注册类帮助程序

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>参数

*Clsid*<br/>
[在]要未注册的对象的 CLSID。

*lpszProgID*<br/>
[在]与对象关联的 ProgID。

*lpszVerindProgID*<br/>
[在]与对象关联的版本无关的 ProgID。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

从系统注册表中删除对象的标准类注册。

[更新注册表类](#updateregistryclass)方法调用`UnregisterClassHelper`。

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a>CCom 模块：：取消注册服务器

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>参数

*bUnRegTypeLib*<br/>
如果为 TRUE，则类型库也未注册。

*pCLSID*<br/>
指向要未注册的对象的 CLSID。 如果 NULL（默认值），则对象映射中的所有对象都将取消注册。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

根据*pCLSID*参数，取消注册单个类对象或对象映射中的所有对象。

`UnregisterServer`将自动调用`DLLUnregisterServer`DLL 或使用`WinMain`命令行选项运行的`/UnregServer`EXE。

有关如何向对象映射添加条目的信息，请参阅[OBJECT_ENTRY_AUTO。](object-map-macros.md#object_entry_auto)

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a>CCom 模块：：更新注册表类

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

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

*Clsid*<br/>
要注册或未注册的对象的 CLSID。

*lpszProgID*<br/>
与对象关联的 ProgID。

*lpszVerindProgID*<br/>
与对象关联的版本无关的 ProgID。

*nDescID*<br/>
对象描述的字符串资源的标识符。

*什德斯茨*<br/>
包含对象描述的字符串。

dwFlags**<br/>
指定要在注册表中输入的线程模型。 可能的值是THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

*b 注册*<br/>
指示是否应注册对象。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果*b寄存器*为 TRUE，则此方法在系统注册表中输入对象的标准类注册。

如果*b 注册*为 FALSE，则删除对象的注册。

根据*b寄存器*的值 ，`UpdateRegistryClass`调用[注册类帮助程序](#registerclasshelper)或[取消注册类帮助程序](#unregisterclasshelper)。

通过指定[DECLARE_REGISTRY](registry-macros.md#declare_registry)宏，`UpdateRegistryClass`将在处理对象映射时自动调用。

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CCom 模块：：从资源中更新注册表

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

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
[在]资源名称。

*nResID*<br/>
[在]资源 ID。

*b 注册*<br/>
[在]指示是否应注册对象。

*pMap条目*<br/>
[在]指向替换映射的指针，存储与脚本的可替换参数关联的值。 ATL 自动`%MODULE%`使用 。 要使用其他可替换参数，请参阅备注了解详细信息。 否则，请使用 NULL 默认值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

运行*lpszRes*或*nResID*指定的资源中包含的脚本。

如果*b寄存器*为 TRUE，则此方法将注册系统注册表中的对象;如果 b 寄存器为 TRUE，则此方法将注册到系统注册表中的对象。否则，它将取消注册该对象。

通过指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)宏，`UpdateRegistryFromResourceD`将在处理对象映射时自动调用。

> [!NOTE]
> 要在运行时替换替换值，请不要指定DECLARE_REGISTRY_RESOURCE或DECLARE_REGISTRY_RESOURCEID宏。 相反，请创建一个`_ATL_REGMAP_ENTRIES`结构数组，其中每个条目包含一个变量占位符，该占位符与值配对，以在运行时替换占位符。 然后调用`UpdateRegistryFromResourceD`，传递*pMapEntries*参数的数组。 这会将结构中的所有`_ATL_REGMAP_ENTRIES`替换值添加到注册器的替换映射中。

> [!NOTE]
> 要静态链接到 ATL 注册表组件 （注册），请参阅[从资源更新注册表 。](#updateregistryfromresources)

有关可替换参数和脚本的详细信息，请参阅[ATL 注册表组件 （注册） 一](../../atl/atl-registry-component-registrar.md)文。

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CCom模块：：从资源更新注册表

从 ATL 7.0`CComModule`起，已过时：有关详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

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
[在]资源名称。

*nResID*<br/>
[在]资源 ID。

*b 注册*<br/>
[在]指示是否应注册资源脚本。

*pMap条目*<br/>
[在]指向替换映射的指针，存储与脚本的可替换参数关联的值。 ATL 自动`%MODULE%`使用 。 要使用其他可替换参数，请参阅备注了解详细信息。 否则，请使用 NULL 默认值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

类似于[更新注册器资源D，](#updateregistryfromresourced)但`UpdateRegistryFromResourceS`创建指向 ATL 注册表组件 （注册器） 的静态链接除外。

`UpdateRegistryFromResourceS`处理对象映射时将自动调用对象映射，前提是您添加到`#define _ATL_STATIC_REGISTRY` *pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）。*

> [!NOTE]
> 要在运行时替换替换值，请不要指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)宏。 相反，请创建一个`_ATL_REGMAP_ENTRIES`结构数组，其中每个条目包含一个变量占位符，该占位符与值配对，以在运行时替换占位符。 然后调用`UpdateRegistryFromResourceS`，传递*pMapEntries*参数的数组。 这会将结构中的所有`_ATL_REGMAP_ENTRIES`替换值添加到注册器的替换映射中。

有关可替换参数和脚本的详细信息，请参阅[ATL 注册表组件 （注册） 一](../../atl/atl-registry-component-registrar.md)文。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
