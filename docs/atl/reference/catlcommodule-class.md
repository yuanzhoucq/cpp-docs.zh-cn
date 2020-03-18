---
title: CAtlComModule 类
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423452"
---
# <a name="catlcommodule-class"></a>CAtlComModule 类

此类实现 COM 服务器模块。

## <a name="syntax"></a>语法

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|构造函数。|
|[CAtlComModule：： ~ CAtlComModule](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|调用此方法以更新对象映射中每个对象的系统注册表。|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|调用此方法可注册类型库。|
|[CAtlComModule::UnregisterServer](#unregisterserver)|调用此方法可取消注册对象映射中的每个对象。|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|调用此方法以注销类型库。|

## <a name="remarks"></a>备注

`CAtlComModule` 实现一个 COM 服务器模块，使客户端能够访问该模块的组件。

此类替换在早期版本的 ATL 中使用的过时[CComModule](../../atl/reference/ccommodule-class.md)类。 有关更多详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="catlcommodule"></a>CAtlComModule::CAtlComModule

构造函数。

```
CAtlComModule() throw();
```

### <a name="remarks"></a>备注

初始化模块。

##  <a name="dtor"></a>CAtlComModule：： ~ CAtlComModule

析构函数。

```
~CAtlComModule();
```

### <a name="remarks"></a>备注

释放所有类工厂。

##  <a name="registerserver"></a>CAtlComModule::RegisterServer

调用此方法以更新对象映射中每个对象的系统注册表。

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>parameters

*bRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。 默认值是 FALSE。

*pCLSID*<br/>
指向要注册的对象的 CLSID。 如果为 NULL （默认值），则将注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用全局函数[AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver)。

##  <a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

调用此方法可注册类型库。

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>parameters

*lpszIndex*<br/>
格式为 "\\\N" 的字符串，其中 N 是 TYPELIB 资源的整数索引。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

将有关类型库的信息添加到系统注册表中。 如果模块实例包含多个类型库，请使用此方法的第一个版本来指定应使用的类型库。

##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer

调用此方法可取消注册对象映射中的每个对象。

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>parameters

*bRegTypeLib*<br/>
如果要注销类型库，则为 TRUE。 默认值是 FALSE。

*pCLSID*<br/>
指向要注销的对象的 CLSID。 如果为 NULL （默认值），则将取消注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用全局函数[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)。

##  <a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

调用此方法以注销类型库。

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>parameters

*lpszIndex*<br/>
格式为 "\\\N" 的字符串，其中 N 是 TYPELIB 资源的整数索引。

### <a name="remarks"></a>备注

从系统注册表中删除有关类型库的信息。 如果模块实例包含多个类型库，请使用此方法的第一个版本来指定应使用的类型库。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

## <a name="see-also"></a>另请参阅

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[类概述](../../atl/atl-class-overview.md)
