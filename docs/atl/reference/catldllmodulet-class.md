---
title: CAtlDllModuleT 类
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: 7a5f8e7e489c8e0d573569ac7c4a8fb63f652732
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319004"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT 类

此类表示 DLL 的模块。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
来自 的类`CAtlDllModuleT`派生自 。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CatlDllModuleT：CatlDllModuleT](#catldllmodulet)|构造函数。|
|[CAtlDllModuleT：_CatlDllModuleT](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CatlDllmodulet：:DllcanUnloadnow](#dllcanunloadnow)|测试是否可以卸载 DLL。|
|[CAtlDllmoduleT：:DllgetclassObject](#dllgetclassobject)|返回类工厂。|
|[CAtlDllModuleT：:DllMain](#dllmain)|动态链接库 （DLL） 的可选入口点。|
|[CAtlDllModuleT：:Dll注册服务器](#dllregisterserver)|将 DLL 中对象的条目添加到系统注册表中。|
|[CAtlDllModuleT：:Dllun寄存器服务器](#dllunregisterserver)|删除 DLL 中对象的系统注册表中的条目。|
|[CAtlDllModuleT：获取类对象](#getclassobject)|返回类工厂。 [DllGetClassObject](#dllgetclassobject)调用 。|

## <a name="remarks"></a>备注

`CAtlDllModuleT`表示动态链接库 （DLL） 的模块，并提供所有 DLL 项目使用的函数。 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)类的这种专业化包括对注册的支持。

有关 ATL 中的模块的详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CatlDllModuleT：CatlDllModuleT

构造函数。

```
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModuleT：_CatlDllModuleT

析构函数。

```
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CatlDllmodulet：:DllcanUnloadnow

测试是否可以卸载 DLL。

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>返回值

如果 DLL 可以卸载，则返回S_OK，如果无法卸载，则返回S_FALSE。

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllmoduleT：:DllgetclassObject

返回类工厂。

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>参数

*rclsid*<br/>
要创建的对象的 CLSID。

*riid*<br/>
请求接口的 IID。

*Ppv*<br/>
指向*riid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppv*设置为 NULL。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT：:DllMain

动态链接库 （DLL） 的可选入口点。

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>参数

*dwReason*<br/>
如果设置为DLL_PROCESS_ATTACH，则禁用DLL_THREAD_ATTACH和DLL_THREAD_DETACH通知调用。

*lp保留*<br/>
保留。

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

禁用DLL_THREAD_ATTACH和DLL_THREAD_DETACH通知调用对于具有许多 DLL、经常创建和删除线程且其 DLL 不需要这些线程级附件/分离通知的多线程应用程序可能是一种有用的优化。

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT：:Dll注册服务器

将 DLL 中对象的条目添加到系统注册表中。

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>参数

*bRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。 默认值为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT：:Dllun寄存器服务器

删除 DLL 中对象的系统注册表中的条目。

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>参数

*bUnRegTypeLib*<br/>
如果要从注册表中删除类型库，则为 TRUE。 默认值为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT：获取类对象

创建指定的 CLSID 的对象。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>参数

*rclsid*<br/>
要创建的对象的 CLSID。

*riid*<br/>
请求接口的 IID。

*Ppv*<br/>
指向*riid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppv*设置为 NULL。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法由[CAtlDllModuleT：:DllGetClassObject](#dllgetclassobject)调用，并包含在向后兼容性方面。

## <a name="see-also"></a>另请参阅

[CAtlModuleT 类](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[模块类](../../atl/atl-module-classes.md)
