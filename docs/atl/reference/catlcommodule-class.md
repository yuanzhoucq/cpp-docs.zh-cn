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
ms.openlocfilehash: 68fdb48edc9304d9d74df6f36bd208cfd35ff307
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321483"
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
|[CAtlCom 模块：CAtlcom 模块](#catlcommodule)|构造函数。|
|[CAtlCom 模块：_CAtlCom 模块](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlCom 模块：：注册服务器](#registerserver)|调用此方法以更新对象映射中每个对象的系统注册表。|
|[CAtlCom 模块：：注册类型 Lib](#registertypelib)|调用此方法以注册类型库。|
|[CAtlCom 模块：：未注册服务器](#unregisterserver)|调用此方法以取消注册对象映射中的每个对象。|
|[CAtlCom 模块：：未注册类型 Lib](#unregistertypelib)|调用此方法以取消注册类型库。|

## <a name="remarks"></a>备注

`CAtlComModule`实现 COM 服务器模块，允许客户端访问模块的组件。

此类将替换早期版本的 ATL 中使用的过时的[CComModule](../../atl/reference/ccommodule-class.md)类。 有关详细信息，请参阅[ATL 模块课程](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlCom 模块：CAtlcom 模块

构造函数。

```
CAtlComModule() throw();
```

### <a name="remarks"></a>备注

初始化模块。

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlCom 模块：_CAtlCom 模块

析构函数。

```
~CAtlComModule();
```

### <a name="remarks"></a>备注

解放所有类工厂。

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlCom 模块：：注册服务器

调用此方法以更新对象映射中每个对象的系统注册表。

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>参数

*bRegTypeLib*<br/>
如果要注册类型库，则为 TRUE。 默认值是 FALSE。

*pCLSID*<br/>
指向要注册的对象的 CLSID。 如果 NULL（默认值），则将注册对象映射中的所有对象。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用全局函数[Atlcommodule 注册服务器](server-registration-global-functions.md#atlcommoduleregisterserver)。

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlCom 模块：：注册类型 Lib

调用此方法以注册类型库。

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>参数

*lpszIndex*<br/>
格式为"\N"\\的字符串，其中 N 是 TYPELIB 资源的整数索引。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

将有关类型库的信息添加到系统注册表。 如果模块实例包含多个类型库，请使用此方法的第一个版本指定应使用的类型库。

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlCom 模块：：未注册服务器

调用此方法以取消注册对象映射中的每个对象。

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>参数

*bRegTypeLib*<br/>
如果类型库要未注册，则为 TRUE。 默认值是 FALSE。

*pCLSID*<br/>
指向要未注册的对象的 CLSID。 如果 NULL（默认值），则对象映射中的所有对象都将取消注册。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用全局函数[AtlcomModuleUn寄存器服务器](server-registration-global-functions.md#atlcommoduleunregisterserver)。

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlCom 模块：：未注册类型 Lib

调用此方法以取消注册类型库。

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>参数

*lpszIndex*<br/>
格式为"\N"\\的字符串，其中 N 是 TYPELIB 资源的整数索引。

### <a name="remarks"></a>备注

从系统注册表中删除有关类型库的信息。 如果模块实例包含多个类型库，请使用此方法的第一个版本指定应使用的类型库。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="see-also"></a>另请参阅

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[类概述](../../atl/atl-class-overview.md)
