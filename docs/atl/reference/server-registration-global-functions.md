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
ms.openlocfilehash: fb6353b52f487d0511c54223fe9e31dab88704b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325929"
---
# <a name="server-registration-global-functions"></a>服务器注册全局函数

这些函数支持在对象映射中注册和取消注册服务器对象。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|调用此函数可在对象映射中注册所有对象。|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|调用此函数可在对象映射中注销所有对象。|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|调用此函数可注册类对象。|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|调用此功能是为了从 COM 模块撤消类对象。|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|调用此函数是为了获取类对象。|

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a>AtlCom模块注册服务器

调用此函数可在对象映射中注册所有对象。

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>参数

*pCom模块*<br/>
指向 COM 模块的指针。

*bRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。

*pCLSID*<br/>
指向要注册的对象的 CLSID。 如果 NULL，则对象映射中的所有对象都将注册。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

`AtlComModuleRegisterServer`走 ATL 自动生成的对象映射，并注册地图中的每个对象。 如果*pCLSID*不是 NULL，则仅注册*pCLSID*引用的对象;否则，所有对象都已注册。

此功能由[CAtlComModule 调用：注册服务器](catlcommodule-class.md#registerserver)。

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a>AtlComModule 未注册服务器

调用此函数可在对象映射中注销所有对象。

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>参数

*pCom模块*<br/>
指向 COM 模块的指针。

*bUnRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。

*pCLSID*<br/>
指向要未注册的对象的 CLSID。 如果 NULL 对象映射中的所有对象都将取消注册。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

`AtlComModuleUnregisterServer`走 ATL 对象映射并取消注册地图中的每个对象。 如果*pCLSID*不是 NULL，则只有*pCLSID*引用的对象未注册;否则，所有对象均未注册。

此函数由[CAtlComModule 调用：：取消注册服务器](catlcommodule-class.md#unregisterserver)。

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a>AtlComModule 注册类对象

调用此函数可注册类对象。

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>参数

*pCom模块*<br/>
指向 COM 模块的指针。

*dwCls上下文*<br/>
指定要在其中运行类对象的上下文。 可能的值是CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER或CLSCTX_LOCAL_SERVER。 有关详细信息，请参阅[CLSCTX。](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx)

dwFlags**<br/>
确定与类对象的连接类型。 可能的值是REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或REGCLS_MULTI_SEPARATE。 有关详细信息，请参阅[REGCLS。](/windows/win32/api/combaseapi/ne-combaseapi-regcls)

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

[CComModule：：注册类对象](ccommodule-class.md#registerclassobjects)（ATL 7.0中过时）和[CAtlExeModuleT：：注册类对象](catlexemodulet-class.md#registerclassobjects)使用此帮助程序函数。

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a>AtlComModule 撤销类对象

调用此函数可从运行对象表中移除类工厂。

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>参数

*pCom模块*<br/>
指向 COM 模块的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

[CComModule：：撤销类对象](ccommodule-class.md#revokeclassobjects)（ATL 7.0 中过时）和[CAtlExeModuleT：：撤销类对象](catlexemodulet-class.md#revokeclassobjects)使用此帮助程序函数。

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject

调用此函数可返回类工厂。

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>参数

*pCom模块*<br/>
指向 COM 模块的指针。

*rclsid*<br/>
要创建的对象的 CLSID。

*riid*<br/>
请求接口的 IID。

*Ppv*<br/>
指向*riid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppv*设置为 NULL。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

[CComModule：获取类对象](ccommodule-class.md#getclassobject)（ATL 7.0中过时）和[CAtlDllModuleT：：获取类对象](catldllmodulet-class.md#getclassobject)使用此帮助程序函数。

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
