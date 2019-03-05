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
ms.openlocfilehash: 2cd207038a92b944bf95575f0e0c820b8f09d615
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272043"
---
# <a name="catlmodulet-class"></a>CAtlModuleT 类

此类实现的 ATL 模块。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类派生自`CAtlModuleT`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|初始化包含当前模块的 GUID 的数据成员。|
|[CAtlModuleT::RegisterAppId](#registerappid)|将该 exe 文件添加到注册表。|
|[CAtlModuleT::RegisterServer](#registerserver)|将服务添加到注册表。|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|从注册表中删除该 exe 文件。|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|从注册表中删除该服务。|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|更新注册表中的 EXE 信息。|

## <a name="remarks"></a>备注

`CAtlModuleT`派生自[CAtlModule](../../atl/reference/catlmodule-class.md)，实现可执行文件 (EXE) 或服务 (EXE) ATL 模块。 可执行模块是为在本地的进程外服务器，而服务模块是一个 Windows 启动时在后台运行的 Windows 应用程序。

`CAtlModuleT` 为初始化、 注册和注销的模块提供支持。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="catlmodulet"></a>  CAtlModuleT::CAtlModuleT

构造函数。

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>备注

调用[CAtlModuleT::InitLibId](#initlibid)。

##  <a name="initlibid"></a>  CAtlModuleT::InitLibId

初始化包含当前模块的 GUID 的数据成员。

```
static void InitLibId() throw();
```

### <a name="remarks"></a>备注

由构造函数调用[CAtlModuleT::CAtlModuleT](#catlmodulet)。

##  <a name="registerappid"></a>  CAtlModuleT::RegisterAppId

将该 exe 文件添加到注册表。

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="registerserver"></a>  CAtlModuleT::RegisterServer

将服务添加到注册表。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>参数

*bRegTypeLib*<br/>
如果类型库的注册，则为 TRUE。 默认值是 FALSE。

*pCLSID*<br/>
指向要注册的对象的 CLSID。 如果将注册为 NULL （默认值），在对象映射中的所有对象。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="unregisterappid"></a>  CAtlModuleT::UnregisterAppId

从注册表中删除该 exe 文件。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="unregisterserver"></a>  CAtlModuleT::UnregisterServer

从注册表中删除该服务。

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>参数

*bUnRegTypeLib*<br/>
如果类型库，则也要注销，则为 TRUE。

*pCLSID*<br/>
指向要注销的对象的 CLSID。 如果为 NULL （默认值），在对象映射中的所有对象将为未注册。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="updateregistryappid"></a>  CAtlModuleT::UpdateRegistryAppId

更新注册表中的 EXE 信息。

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>参数

*bRegister*<br/>
保留。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

## <a name="see-also"></a>请参阅

[CAtlModule 类](../../atl/reference/catlmodule-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[Module 类](../../atl/atl-module-classes.md)
