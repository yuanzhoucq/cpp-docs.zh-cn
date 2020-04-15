---
title: CAtlModuleT 类
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: bf64c073249b7426fafb430a708573d9d06d11fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321410"
---
# <a name="catlmodulet-class"></a>CAtlModuleT 类

此类实现 ATL 模块。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>参数

*T*<br/>
来自 的类`CAtlModuleT`派生自 。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlModuleT：CAtlModuleT](#catlmodulet)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Catlmodulet：：InitLibId](#initlibid)|初始化包含当前模块 GUID 的数据成员。|
|[CAtlModuleT：：注册应用程序](#registerappid)|将 EXE 添加到注册表。|
|[CAtlModuleT：：注册服务器](#registerserver)|将服务添加到注册表。|
|[CAtlModuleT：：未注册AppId](#unregisterappid)|从注册表中删除 EXE。|
|[CAtlModuleT：：未注册服务器](#unregisterserver)|从注册表中删除服务。|
|[CAtlModuleT：：更新注册应用程序](#updateregistryappid)|更新注册表中的 EXE 信息。|

## <a name="remarks"></a>备注

`CAtlModuleT`，派生自[CAtlModule](../../atl/reference/catlmodule-class.md)， 实现可执行 （EXE） 或服务 （EXE） ATL 模块。 可执行模块是本地、进程外服务器，而服务模块是 Windows 应用程序，在 Windows 启动时在后台运行。

`CAtlModuleT`支持模块的初始化、注册和取消注册。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT：CAtlModuleT

构造函数。

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>备注

调用[Catlmodulet：initLibId](#initlibid)。

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>Catlmodulet：：InitLibId

初始化包含当前模块 GUID 的数据成员。

```
static void InitLibId() throw();
```

### <a name="remarks"></a>备注

由构造函数[CAtlModuleT 调用：CAtlModuleT](#catlmodulet)。

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT：：注册应用程序

将 EXE 添加到注册表。

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT：：注册服务器

将服务添加到注册表。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>参数

*bRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。 默认值是 FALSE。

*pCLSID*<br/>
指向要注册的对象的 CLSID。 如果 NULL（默认值），则将注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT：：未注册AppId

从注册表中删除 EXE。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT：：未注册服务器

从注册表中删除服务。

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>参数

*bUnRegTypeLib*<br/>
如果类型库也要取消注册，则为 TRUE。

*pCLSID*<br/>
指向要未注册的对象的 CLSID。 如果 NULL（默认值），则对象映射中的所有对象都将取消注册。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT：：更新注册应用程序

更新注册表中的 EXE 信息。

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>参数

*b 注册*<br/>
保留。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="see-also"></a>另请参阅

[CAtlModule 类](../../atl/reference/catlmodule-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[模块类](../../atl/atl-module-classes.md)
