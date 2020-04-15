---
title: CAtlModule 类
ms.date: 11/04/2016
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: 378c8634e00935c622f0bf5d06a4f6c50cc60cb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321429"
---
# <a name="catlmodule-class"></a>CAtlModule 类

此类提供多个 ATL 模块类使用的方法。

## <a name="syntax"></a>语法

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtl 模块：CAtl 模块](#catlmodule)|构造函数。|
|[CAtl 模块：_CAtl 模块](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtl 模块：添加公共 RGS 替换](#addcommonrgsreplacements)|重写此方法以将参数添加到 ATL 注册表组件 （注册商） 替换映射。|
|[CAtl 模块：：添加TermFunc](#addtermfunc)|添加在模块终止时要调用的新功能。|
|[CAtl 模块：获取 GITPtr](#getgitptr)|返回全局接口指针。|
|[CAtl 模块：：获取锁定计数](#getlockcount)|返回锁计数。|
|[CAtl 模块：锁定](#lock)|增加锁计数。|
|[CAtl 模块：：学期](#term)|释放所有数据成员。|
|[CAtl 模块：解锁](#unlock)|减少锁计数。|
|[CAtlModule：：更新注册从资源D](#updateregistryfromresourced)|运行指定资源中包含的脚本以注册或取消注册对象。|
|[CAtlModule：从资源帮助程序更新注册](#updateregistryfromresourcedhelper)|调用此方法`UpdateRegistryFromResourceD`以执行注册表更新。|
|[CAtlModule：从资源更新注册](#updateregistryfromresources)|运行指定资源中包含的脚本以注册或取消注册对象。 此方法静态链接到 ATL 注册表组件。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAtlModule：m_libid](#m_libid)|包含当前模块的 GUID。|
|[CAtlModule：m_pGIT](#m_pgit)|指向全局接口表的指针。|

## <a name="remarks"></a>备注

此类分别由[CAtlDllModuleT 类](../../atl/reference/catldllmodulet-class.md)[、CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)和[CAtlServiceModuleT 类](../../atl/reference/catlservicemodulet-class.md)使用，分别为 DLL 应用程序、EXE 应用程序和 Windows 服务提供支持。

有关 ATL 中的模块的详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

此类将替换早期版本的 ATL 中使用的过时的[CComModule 类](../../atl/reference/ccommodule-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtl 模块：添加公共 RGS 替换

重写此方法以将参数添加到 ATL 注册表组件 （注册商） 替换映射。

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>参数

*p 注册商*<br/>
保留。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

可替换参数允许注册器的客户端指定运行时数据。 为此，注册器维护一个替换映射，在其中输入与脚本中可替换参数关联的值。 注册器在运行时进行这些条目。

有关详细信息，请参阅["使用可替换参数（注册器的预处理器）"](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)主题。

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtl 模块：：添加TermFunc

添加在模块终止时要调用的新功能。

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>参数

*普丰克*<br/>
指向要添加的函数的指针。

*dw*<br/>
用户定义的数据，传递给函数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtl 模块：CAtl 模块

构造函数。

```
CAtlModule() throw();
```

### <a name="remarks"></a>备注

初始化数据成员并围绕模块的线程启动关键部分。

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtl 模块：_CAtl 模块

析构函数。

```
~CAtlModule() throw();
```

### <a name="remarks"></a>备注

释放所有数据成员。

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtl 模块：获取 GITPtr

检索指向全局接口表的指针。

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>参数

*ppGIT*<br/>
指向将接收指向全局接口表的指针的变量的指针。

### <a name="return-value"></a>返回值

返回成功时S_OK，或失败时返回错误代码。 如果*ppGIT*等于 NULL，则返回E_POINTER。

### <a name="remarks"></a>备注

如果全局接口表对象不存在，则创建该对象，其地址存储在成员变量[CAtlModule：：：m_pGIT](#m_pgit)。

在调试生成中，如果*ppGIT*等于 NULL，或者无法获取全局接口表指针，则会发生断言错误。

有关全局接口表的信息，请参阅[IGlobal 接口表](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable)。

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtl 模块：：获取锁定计数

返回锁计数。

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>返回值

返回锁计数。 此值可用于诊断和调试。

## <a name="catlmodulelock"></a><a name="lock"></a>CAtl 模块：锁定

增加锁计数。

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>返回值

增加锁计数并返回更新的值。 此值可用于诊断和调试。

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModule：m_libid

包含当前模块的 GUID。

```
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModule：m_pGIT

指向全局接口表的指针。

```
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtl 模块：：学期

释放所有数据成员。

```
void Term() throw();
```

### <a name="remarks"></a>备注

释放所有数据成员。 此方法由析构函数调用。

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtl 模块：解锁

减少锁计数。

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

正在撤销锁计数并返回更新的值。 此值可用于诊断和调试。

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule：：更新注册从资源D

运行指定资源中包含的脚本以注册或取消注册对象。

```
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>参数

*lpszRes*<br/>
资源名称。

*nResID*<br/>
资源 ID。

*b 注册*<br/>
如果应注册对象，则为 TRUE;否则。

*pMap条目*<br/>
指向替换映射的指针，存储与脚本的可替换参数关联的值。 ATL 自动使用 %MODULE%。 要使用其他可替换参数，请参阅[CAtlModule：：添加通用 RGS 替换](#addcommonrgsreplacements)项 。 否则，请使用 NULL 默认值。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

运行*lpszRes 或 nResID*指定的资源中包含的脚本。 如果*b寄存器*为 TRUE，则此方法将注册系统注册表中的对象;如果 b 寄存器为 TRUE，则此方法将注册到系统注册表中的对象。否则，它将对象从注册表中删除。

要静态链接到 ATL 注册表组件 （注册），请参阅[CAtlModule：：更新注册表来自资源](#updateregistryfromresources)。

此方法调用[CAtlModule：：从资源DHelper](#updateregistryfromresourcedhelper)和 IRegistrar 更新注册[：：资源未注册](iregistrar-class.md#resourceunregister)。

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule：从资源帮助程序更新注册

调用此方法`UpdateRegistryFromResourceD`以执行注册表更新。

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>参数

*lpszRes*<br/>
资源名称。

*b 注册*<br/>
指示是否应注册对象。

*pMap条目*<br/>
指向替换映射的指针，存储与脚本的可替换参数关联的值。 ATL 自动使用 %MODULE%。 要使用其他可替换参数，请参阅[CAtlModule：：添加通用 RGS 替换](#addcommonrgsreplacements)项 。 否则，请使用 NULL 默认值。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法提供[CAtlModule 的实现：：更新注册从资源D。](#updateregistryfromresourced)

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule：从资源更新注册

运行指定资源中包含的脚本以注册或取消注册对象。 此方法静态链接到 ATL 注册表组件。

```
HRESULT WINAPI UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>参数

*nResID*<br/>
资源 ID。

*lpszRes*<br/>
资源名称。

*b 注册*<br/>
指示是否应注册资源脚本。

*pMap条目*<br/>
指向替换映射的指针，存储与脚本的可替换参数关联的值。 ATL 自动使用 %MODULE%。 要使用其他可替换参数，请参阅[CAtlModule：：添加通用 RGS 替换](#addcommonrgsreplacements)项 。 否则，请使用 NULL 默认值。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

类似于[CAtlModule：：更新注册注册从资源D，](#updateregistryfromresourced)除了`CAtlModule::UpdateRegistryFromResourceS`创建一个静态链接到 ATL 注册表组件 （注册）。

## <a name="see-also"></a>另请参阅

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[模块类](../../atl/atl-module-classes.md)<br/>
[注册表组件（注册器）](../../atl/atl-registry-component-registrar.md)
