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
ms.openlocfilehash: f01734d4ec9de323325dc793756f421388542ef2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246997"
---
# <a name="catlmodule-class"></a>CAtlModule 类

此类提供使用多个 ATL module 类的方法。

## <a name="syntax"></a>语法

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|构造函数。|
|[CAtlModule::~CAtlModule](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|重写此方法以将参数添加到 ATL 注册表组件 （注册器） 替换映射。|
|[CAtlModule::AddTermFunc](#addtermfunc)|添加了一个新的函数，该模块终止时要调用。|
|[CAtlModule::GetGITPtr](#getgitptr)|返回全局接口指针。|
|[CAtlModule::GetLockCount](#getlockcount)|返回的锁计数。|
|[CAtlModule::Lock](#lock)|锁计数递增。|
|[CAtlModule::Term](#term)|释放所有数据成员。|
|[CAtlModule::Unlock](#unlock)|减少锁计数。|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|在运行注册或注销对象指定的资源中包含的脚本。|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|调用此方法`UpdateRegistryFromResourceD`执行注册表更新。|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|在运行注册或注销对象指定的资源中包含的脚本。 此方法以静态方式链接到 ATL 注册表组件。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|包含当前模块的 GUID。|
|[CAtlModule::m_pGIT](#m_pgit)|指向全局接口表的指针。|

## <a name="remarks"></a>备注

使用此类[CAtlDllModuleT 类](../../atl/reference/catldllmodulet-class.md)， [CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)，并[CAtlServiceModuleT 类](../../atl/reference/catlservicemodulet-class.md)为 DLL 应用程序，EXE 应用程序提供支持和Windows 服务，分别。

在 ATL 中的模块的详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

此类替换已过时[CComModule 类](../../atl/reference/ccommodule-class.md)使用在早期版本的 atl。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements

重写此方法以将参数添加到 ATL 注册表组件 （注册器） 替换映射。

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>参数

*pRegistrar*<br/>
保留。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

可替换参数允许注册机构的客户端可以指定运行时数据。 若要执行此操作，在注册机构来维护替换映射到其中进入与您的脚本中的可替换参数关联的值。 在注册机构将在运行时这些项。

请参阅主题[使用可替换参数 （注册机构的预处理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)的更多详细信息。

##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc

添加了一个新的函数，该模块终止时要调用。

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>参数

*pFunc*<br/>
若要添加的函数指针。

*dw*<br/>
用户定义数据传递给函数。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="catlmodule"></a>  CAtlModule::CAtlModule

构造函数。

```
CAtlModule() throw();
```

### <a name="remarks"></a>备注

初始化数据成员，并启动围绕模块的线程的临界区。

##  <a name="dtor"></a>  CAtlModule:: ~ CAtlModule

析构函数。

```
~CAtlModule() throw();
```

### <a name="remarks"></a>备注

释放所有数据成员。

##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr

检索指向全局接口表的指针。

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>参数

*ppGIT*<br/>
指向将接收指向全局接口表的指针的变量。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败的错误代码。 如果，则返回 E_POINTER *ppGIT*等于 NULL。

### <a name="remarks"></a>备注

如果全局接口表对象不存在，它将创建，并且其地址存储在成员变量[CAtlModule::m_pGIT](#m_pgit)。

在调试版本中，如果出现断言错误*ppGIT*等于 NULL，或如果无法获取全局接口表指针。

请参阅[IGlobalInterfaceTable](/windows/desktop/api/objidl/nn-objidl-iglobalinterfacetable)有关全局接口表的信息。

##  <a name="getlockcount"></a>  CAtlModule::GetLockCount

返回的锁计数。

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>返回值

返回的锁计数。 此值可能有用的诊断和调试。

##  <a name="lock"></a>  CAtlModule::Lock

锁计数递增。

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>返回值

锁计数递增，并返回更新后的值。 此值可能有用的诊断和调试。

##  <a name="m_libid"></a>  CAtlModule::m_libid

包含当前模块的 GUID。

```
static GUID m_libid;
```

##  <a name="m_pgit"></a>  CAtlModule::m_pGIT

指向全局接口表的指针。

```
IGlobalInterfaceTable* m_pGIT;
```

##  <a name="term"></a>  CAtlModule::Term

释放所有数据成员。

```
void Term() throw();
```

### <a name="remarks"></a>备注

释放所有数据成员。 析构函数调用此方法。

##  <a name="unlock"></a>  CAtlModule::Unlock

减少锁计数。

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

减少锁计数，并返回更新后的值。 此值可能有用的诊断和调试。

##  <a name="updateregistryfromresourced"></a>  CAtlModule::UpdateRegistryFromResourceD

在运行注册或注销对象指定的资源中包含的脚本。

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
资源 id。

*bRegister*<br/>
如果应注册对象; 则为 TRUEFALSE 否则为。

*pMapEntries*<br/>
指向存储脚本的可替换参数与关联的值替换地图的指针。 ATL 自动使用 %模块 %。 若要使用其他可替换参数，请参阅[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否则，使用 NULL 默认值。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

运行指定的资源中包含的脚本*lpszRes 或 nResID*。 如果*bRegister*为 TRUE 时，此方法在系统注册表中注册该对象; 否则它将删除该对象从注册表。

若要以静态方式链接到 ATL 注册表组件 （注册器），请参阅[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)。

此方法调用[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)并[IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister)。

##  <a name="updateregistryfromresourcedhelper"></a>  CAtlModule::UpdateRegistryFromResourceDHelper

调用此方法`UpdateRegistryFromResourceD`执行注册表更新。

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>参数

*lpszRes*<br/>
资源名称。

*bRegister*<br/>
指示是否应注册对象。

*pMapEntries*<br/>
指向存储脚本的可替换参数与关联的值替换地图的指针。 ATL 自动使用 %模块 %。 若要使用其他可替换参数，请参阅[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否则，使用 NULL 默认值。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

此方法提供的实现[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)。

##  <a name="updateregistryfromresources"></a>  CAtlModule::UpdateRegistryFromResourceS

在运行注册或注销对象指定的资源中包含的脚本。 此方法以静态方式链接到 ATL 注册表组件。

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
资源 id。

*lpszRes*<br/>
资源名称。

*bRegister*<br/>
指示是否应注册为资源脚本。

*pMapEntries*<br/>
指向存储脚本的可替换参数与关联的值替换地图的指针。 ATL 自动使用 %模块 %。 若要使用其他可替换参数，请参阅[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否则，使用 NULL 默认值。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

类似于[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)除`CAtlModule::UpdateRegistryFromResourceS`创建静态链接到 ATL 注册表组件 （注册器）。

## <a name="see-also"></a>请参阅

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[Module 类](../../atl/atl-module-classes.md)<br/>
[注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)
