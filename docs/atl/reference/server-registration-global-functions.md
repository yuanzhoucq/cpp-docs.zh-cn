---
title: 服务器注册全局函数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: f9c3697259e1cee2b1107ded785ca583d730b55e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863154"
---
# <a name="server-registration-global-functions"></a>服务器注册全局函数

这些函数提供对在对象映射中注册和注销服务器对象的支持。

> [!IMPORTANT]
>  下表中列出的函数不能用于在 Windows 运行时中执行的应用程序。

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|调用此函数可在对象映射中注册所有对象。|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|调用此函数可在对象映射中注销所有对象。|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|调用此函数可注册类对象。|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|调用此函数可从 COM 模块中撤消类对象。|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|调用此函数可获取类对象。|

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer

调用此函数可在对象映射中注册所有对象。

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>parameters

*pComModule*<br/>
指向 COM 模块的指针。

*bRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。

*pCLSID*<br/>
指向要注册的对象的 CLSID。 如果为 NULL，则将注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

`AtlComModuleRegisterServer` 将遍历 ATL 自动生成的对象映射，并在映射中注册每个对象。 如果*pCLSID*不为 NULL，则仅注册由*pCLSID*引用的对象;否则，将注册所有的对象。

此函数由[CAtlComModule：： RegisterServer](catlcommodule-class.md#registerserver)调用。

##  <a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer

调用此函数可在对象映射中注销所有对象。

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>parameters

*pComModule*<br/>
指向 COM 模块的指针。

*bUnRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。

*pCLSID*<br/>
指向要注销的对象的 CLSID。 如果为 NULL，则将取消注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

`AtlComModuleUnregisterServer` 将遍历 ATL 对象映射，并取消注册映射中的每个对象。 如果*pCLSID*不为 NULL，则仅注销*pCLSID*引用的对象;否则，将注销所有对象。

此函数由[CAtlComModule：： UnregisterServer](catlcommodule-class.md#unregisterserver)调用。

##  <a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects

调用此函数可注册类对象。

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>parameters

*pComModule*<br/>
指向 COM 模块的指针。

*dwClsContext*<br/>
指定要在其中运行类对象的上下文。 可能的值为 CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。 有关更多详细信息，请参阅[CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) 。

dwFlags<br/>
确定类对象的连接类型。 可能的值为 REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。 有关更多详细信息，请参阅[REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此 helper 函数使用[CComModule：： RegisterClassObjects](ccommodule-class.md#registerclassobjects) （在 ATL 7.0 中已过时）和[Catlexemodulet 用作：： RegisterClassObjects](catlexemodulet-class.md#registerclassobjects)。

##  <a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects

调用此函数可从运行对象表中移除类工厂。

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>parameters

*pComModule*<br/>
指向 COM 模块的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此 helper 函数使用[CComModule：： RevokeClassObjects](ccommodule-class.md#revokeclassobjects) （在 ATL 7.0 中已过时）和[Catlexemodulet 用作：： RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects)。

##  <a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject

调用此函数可返回类工厂。

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>parameters

*pComModule*<br/>
指向 COM 模块的指针。

*rclsid*<br/>
要创建的对象的 CLSID。

*riid*<br/>
所请求的接口的 IID。

*ppv*<br/>
指向由*riid*标识的接口指针的指针。 如果对象不支持此接口，则将*ppv*设置为 NULL。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此 helper 函数使用[CComModule：： GetClassObject](ccommodule-class.md#getclassobject) （在 ATL 7.0 中已过时）和[Catldllmodulet 用作基类：： GetClassObject](catldllmodulet-class.md#getclassobject)。

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
