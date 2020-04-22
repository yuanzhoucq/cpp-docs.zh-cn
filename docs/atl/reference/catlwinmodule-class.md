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
ms.openlocfilehash: e131ca1b4eb6e320d533ad1292c23add6ffa46e5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748552"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule 类

此类支持 ATL 窗口组件。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlWin 模块：CAtlWin 模块](#catlwinmodule)|构造函数。|
|[CAtlWin 模块：*CAtlWin 模块](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlWin模块：：添加创建WndData](#addcreatewnddata)|添加数据对象。|
|[CAtlWin 模块：：提取创建WndData](#extractcreatewnddata)|返回指向窗口模块数据对象的指针。|

## <a name="remarks"></a>备注

此类支持所有需要窗口功能的 ATL 类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWin模块：：添加创建WndData

此方法初始化和添加`_AtlCreateWndData`结构。

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>参数

*pData*<br/>
指向要初始`_AtlCreateWndData`化并添加到当前模块的结构的指针。

*pObject*<br/>
指向对象的**此**指针。

### <a name="remarks"></a>备注

此方法调用[AtlWinModuleAddCreatewnddata，该数据](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata)初始化了[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构。 此结构将存储**此**指针，用于在窗口过程中获取类实例。

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWin 模块：CAtlWin 模块

构造函数。

```
CAtlWinModule();
```

### <a name="remarks"></a>备注

如果初始化失败，将引发**EXCEPTION_NONCONTINUABLE**异常。

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWin 模块：*CAtlWin 模块

析构函数。

```
~CAtlWinModule();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWin 模块：：提取创建WndData

此方法返回指向结构的`_AtlCreateWndData`指针。

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>返回值

返回指向以前添加的`_AtlCreateWndData` [CAtlWinModule：：addCreateWndData](#addcreatewnddata)（）或 NULL（如果没有可用对象）的结构的指针。

## <a name="see-also"></a>请参阅

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[模块类](../../atl/atl-module-classes.md)
