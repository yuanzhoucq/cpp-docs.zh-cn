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
ms.openlocfilehash: 798e94aed3bbd98108866ce0a1810485bd68699b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423422"
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
|[CAtlModule::CAtlModule](#catlmodule)|构造函数。|
|[CAtlModule：： ~ CAtlModule](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|重写此方法以将参数添加到 ATL 注册表组件（注册器）替换映射。|
|[CAtlModule::AddTermFunc](#addtermfunc)|添加模块终止时要调用的新函数。|
|[CAtlModule::GetGITPtr](#getgitptr)|返回全局接口指针。|
|[CAtlModule::GetLockCount](#getlockcount)|返回锁计数。|
|[CAtlModule：： Lock](#lock)|递增锁计数。|
|[CAtlModule：： Term](#term)|释放所有数据成员。|
|[CAtlModule：： Unlock](#unlock)|减少锁计数。|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|运行指定资源中包含的脚本，以注册或取消注册对象。|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|此方法由 `UpdateRegistryFromResourceD` 调用以执行注册表更新。|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|运行指定资源中包含的脚本，以注册或取消注册对象。 此方法静态链接到 ATL 注册表组件。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAtlModule：： m_libid](#m_libid)|包含当前模块的 GUID。|
|[CAtlModule：： m_pGIT](#m_pgit)|指向全局接口表的指针。|

## <a name="remarks"></a>备注

此类由[Catldllmodulet 用作基类类](../../atl/reference/catldllmodulet-class.md)、 [Catlexemodulet 用作类](../../atl/reference/catlexemodulet-class.md)和[CATLSERVICEMODULET 类](../../atl/reference/catlservicemodulet-class.md)用于分别为 DLL 应用程序、EXE 应用程序和 Windows 服务提供支持。

有关 ATL 中的模块的详细信息，请参阅[Atl Module 类](../../atl/atl-module-classes.md)。

此类替换在早期版本的 ATL 中使用的过时[CComModule 类](../../atl/reference/ccommodule-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements

重写此方法以将参数添加到 ATL 注册表组件（注册器）替换映射。

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>parameters

*pRegistrar*<br/>
保留。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

可替换参数允许注册机构的客户端指定运行时数据。 为此，注册机构将维护一个替换地图，其中输入与脚本中的可替换参数相关联的值。 注册器会在运行时生成这些项。

有关更多详细信息，请参阅主题[使用可替换参数（注册器的预处理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) 。

##  <a name="addtermfunc"></a>CAtlModule::AddTermFunc

添加模块终止时要调用的新函数。

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>parameters

*pFunc*<br/>
指向要添加的函数的指针。

*dw*<br/>
用户定义的数据，传递到函数。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="catlmodule"></a>CAtlModule::CAtlModule

构造函数。

```
CAtlModule() throw();
```

### <a name="remarks"></a>备注

初始化数据成员，并在模块的线程周围启动关键部分。

##  <a name="dtor"></a>CAtlModule：： ~ CAtlModule

析构函数。

```
~CAtlModule() throw();
```

### <a name="remarks"></a>备注

释放所有数据成员。

##  <a name="getgitptr"></a>CAtlModule::GetGITPtr

检索指向全局接口表的指针。

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>parameters

*ppGIT*<br/>
指向变量的指针，该变量将接收指向全局接口表的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误代码。 如果*ppGIT*等于 NULL，则返回 E_POINTER。

### <a name="remarks"></a>备注

如果全局接口表对象不存在，则将创建该对象，并将其地址存储在成员变量[CAtlModule：： m_pGIT](#m_pgit)中。

在调试版本中，如果*ppGIT*等于 NULL，则将发生断言错误，如果无法获取全局接口表指针，则将发生断言错误。

有关全局接口表的信息，请参阅[IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) 。

##  <a name="getlockcount"></a>CAtlModule::GetLockCount

返回锁计数。

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>返回值

返回锁计数。 此值可能适用于诊断和调试。

##  <a name="lock"></a>CAtlModule：： Lock

递增锁计数。

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>返回值

递增锁计数并返回更新的值。 此值可能适用于诊断和调试。

##  <a name="m_libid"></a>CAtlModule：： m_libid

包含当前模块的 GUID。

```
static GUID m_libid;
```

##  <a name="m_pgit"></a>CAtlModule：： m_pGIT

指向全局接口表的指针。

```
IGlobalInterfaceTable* m_pGIT;
```

##  <a name="term"></a>CAtlModule：： Term

释放所有数据成员。

```
void Term() throw();
```

### <a name="remarks"></a>备注

释放所有数据成员。 此方法由析构函数调用。

##  <a name="unlock"></a>CAtlModule：： Unlock

减少锁计数。

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

减少锁计数并返回更新的值。 此值可能适用于诊断和调试。

##  <a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

运行指定资源中包含的脚本，以注册或取消注册对象。

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

### <a name="parameters"></a>parameters

*lpszRes*<br/>
资源名称。

*nResID*<br/>
资源 ID。

*bRegister*<br/>
如果应注册该对象，则为 TRUE; 否则为。否则为 FALSE。

*pMapEntries*<br/>
指向替换映射的指针，该指针存储与脚本的可替换参数关联的值。 ATL 自动使用% MODULE%。 若要使用其他可替换参数，请参阅[CAtlModule：： AddCommonRGSReplacements](#addcommonrgsreplacements)。 否则，请使用 NULL 默认值。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

运行*lpszRes 或 nResID*指定的资源中包含的脚本。 如果*bRegister*为 TRUE，则此方法将在系统注册表中注册对象;否则，将从注册表中删除对象。

若要以静态方式链接到 ATL 注册表组件（注册器），请参阅[CAtlModule：： UpdateRegistryFromResourceS](#updateregistryfromresources)。

此方法调用[CAtlModule：： UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)和[IRegistrar：： ResourceUnregister](iregistrar-class.md#resourceunregister)。

##  <a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

此方法由 `UpdateRegistryFromResourceD` 调用以执行注册表更新。

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>parameters

*lpszRes*<br/>
资源名称。

*bRegister*<br/>
指示是否应注册对象。

*pMapEntries*<br/>
指向替换映射的指针，该指针存储与脚本的可替换参数关联的值。 ATL 自动使用% MODULE%。 若要使用其他可替换参数，请参阅[CAtlModule：： AddCommonRGSReplacements](#addcommonrgsreplacements)。 否则，请使用 NULL 默认值。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法提供[CAtlModule：： UpdateRegistryFromResourceD](#updateregistryfromresourced)的实现。

##  <a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

运行指定资源中包含的脚本，以注册或取消注册对象。 此方法静态链接到 ATL 注册表组件。

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

### <a name="parameters"></a>parameters

*nResID*<br/>
资源 ID。

*lpszRes*<br/>
资源名称。

*bRegister*<br/>
指示是否应注册资源脚本。

*pMapEntries*<br/>
指向替换映射的指针，该指针存储与脚本的可替换参数关联的值。 ATL 自动使用% MODULE%。 若要使用其他可替换参数，请参阅[CAtlModule：： AddCommonRGSReplacements](#addcommonrgsreplacements)。 否则，请使用 NULL 默认值。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

类似于[CAtlModule：： UpdateRegistryFromResourceD](#updateregistryfromresourced) ，`CAtlModule::UpdateRegistryFromResourceS` 创建指向 ATL 注册表组件（注册器）的静态链接。

## <a name="see-also"></a>另请参阅

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[Module 类](../../atl/atl-module-classes.md)<br/>
[注册表组件（注册器）](../../atl/atl-registry-component-registrar.md)
