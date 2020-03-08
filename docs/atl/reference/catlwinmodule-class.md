---
title: CAtlWinModule 类
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: d0bc98fa48f84e67ab38106dea3fe22d5ad1757d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857346"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule 类

此类提供对 ATL 窗口化组件的支持。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|构造函数。|
|[CAtlWinModule：： ~ CAtlWinModule](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|添加数据对象。|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|返回一个指向窗口模块数据对象的指针。|

## <a name="remarks"></a>备注

此类为需要窗口化功能的所有 ATL 类提供支持。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

此方法初始化并添加 `_AtlCreateWndData` 结构。

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>参数

*pData*<br/>
一个指针，指向要初始化并添加到当前模块的 `_AtlCreateWndData` 结构。

*pObject*<br/>
指向对象的**this**指针的指针。

### <a name="remarks"></a>备注

此方法调用[AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) ，后者初始化[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构。 此结构将存储用于在窗口过程中获取类实例**的指针。**

##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

构造函数。

```
CAtlWinModule();
```

### <a name="remarks"></a>备注

如果初始化失败，则会引发**EXCEPTION_NONCONTINUABLE**异常。

##  <a name="dtor"></a>CAtlWinModule：： ~ CAtlWinModule

析构函数。

```
~CAtlWinModule();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

此方法返回指向 `_AtlCreateWndData` 结构的指针。

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>返回值

返回一个指向先前用[CAtlWinModule：： AddCreateWndData](#addcreatewnddata)添加的 `_AtlCreateWndData` 结构的指针; 如果没有可用的对象，则返回 NULL。

## <a name="see-also"></a>另请参阅

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[Module 类](../../atl/atl-module-classes.md)
