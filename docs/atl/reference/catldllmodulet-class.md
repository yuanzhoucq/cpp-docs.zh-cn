---
title: Catldllmodulet 用作基类类
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
ms.openlocfilehash: be42915c6c2e941bc5fc1de78c5c7ac26ccca6e2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423440"
---
# <a name="catldllmodulet-class"></a>Catldllmodulet 用作基类类

此类表示 DLL 的模块。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>parameters

*T*<br/>
派生自 `CAtlDllModuleT`的类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Catldllmodulet 用作基类：： Catldllmodulet 用作基类](#catldllmodulet)|构造函数。|
|[Catldllmodulet 用作基类：： ~ Catldllmodulet 用作基类](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Catldllmodulet 用作基类：:D llCanUnloadNow](#dllcanunloadnow)|测试 DLL 是否可以卸载。|
|[Catldllmodulet 用作基类：:D llGetClassObject](#dllgetclassobject)|返回类工厂。|
|[Catldllmodulet 用作基类：:D llMain](#dllmain)|动态链接库（DLL）中的可选入口点。|
|[Catldllmodulet 用作基类：:D llRegisterServer](#dllregisterserver)|向 DLL 中对象的系统注册表中添加项。|
|[Catldllmodulet 用作基类：:D llUnregisterServer](#dllunregisterserver)|删除 DLL 中对象的系统注册表项。|
|[Catldllmodulet 用作基类：： GetClassObject](#getclassobject)|返回类工厂。 由[DllGetClassObject](#dllgetclassobject)调用。|

## <a name="remarks"></a>备注

`CAtlDllModuleT` 表示动态链接库（DLL）的模块，并提供所有 DLL 项目使用的函数。 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)类的这一特殊化包括对注册的支持。

有关 ATL 中的模块的详细信息，请参阅[Atl Module 类](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="catldllmodulet"></a>Catldllmodulet 用作基类：： Catldllmodulet 用作基类

构造函数。

```
CAtlDllModuleT() throw();
```

##  <a name="dtor"></a>Catldllmodulet 用作基类：： ~ Catldllmodulet 用作基类

析构函数。

```
~CAtlDllModuleT() throw();
```

##  <a name="dllcanunloadnow"></a>Catldllmodulet 用作基类：:D llCanUnloadNow

测试 DLL 是否可以卸载。

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>返回值

如果可以卸载 DLL，则返回 S_OK; 否则返回 S_FALSE。

##  <a name="dllgetclassobject"></a>Catldllmodulet 用作基类：:D llGetClassObject

返回类工厂。

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>parameters

*rclsid*<br/>
要创建的对象的 CLSID。

*riid*<br/>
所请求的接口的 IID。

*ppv*<br/>
指向由*riid*标识的接口指针的指针。 如果对象不支持此接口，则将*ppv*设置为 NULL。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="dllmain"></a>Catldllmodulet 用作基类：:D llMain

动态链接库（DLL）中的可选入口点。

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>parameters

*dwReason*<br/>
如果设置为 DLL_PROCESS_ATTACH，将禁用 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知调用。

*lpReserved*<br/>
保留。

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

禁用 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知调用对于具有多个 Dll 的多线程应用程序来说是一个非常有用的优化，这些应用程序经常创建和删除线程，其 Dll 不需要这些分离的线程级通知。

##  <a name="dllregisterserver"></a>Catldllmodulet 用作基类：:D llRegisterServer

向 DLL 中对象的系统注册表中添加项。

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>parameters

*bRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。 默认值为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="dllunregisterserver"></a>Catldllmodulet 用作基类：:D llUnregisterServer

删除 DLL 中对象的系统注册表项。

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>parameters

*bUnRegTypeLib*<br/>
如果要从注册表中删除类型库，则为 TRUE。 默认值为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="getclassobject"></a>Catldllmodulet 用作基类：： GetClassObject

创建指定 CLSID 的对象。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>parameters

*rclsid*<br/>
要创建的对象的 CLSID。

*riid*<br/>
所请求的接口的 IID。

*ppv*<br/>
指向由*riid*标识的接口指针的指针。 如果对象不支持此接口，则将*ppv*设置为 NULL。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法由[catldllmodulet 用作基类：:D llgetclassobject](#dllgetclassobject)调用，包括在内以实现向后兼容性。

## <a name="see-also"></a>另请参阅

[CAtlModuleT 类](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[Module 类](../../atl/atl-module-classes.md)
