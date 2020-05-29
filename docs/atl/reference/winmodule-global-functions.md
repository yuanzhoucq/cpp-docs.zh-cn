---
title: WinModule 全局函数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 3d7d001a2835514cc5385a7069c0bcda58cdd88e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329362"
---
# <a name="winmodule-global-functions"></a>WinModule 全局函数

这些函数为`_AtlCreateWndData`结构操作提供支持。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函数用于初始化和添加`_AtlCreateWndData` 结构。|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|调用此函数可提取现有 `_AtlCreateWndData` 结构。|

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreatewndData

此函数用于初始化和添加`_AtlCreateWndData` 结构。

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>参数

*pWinModule*<br/>
指向模块[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构的指针。

*pData*<br/>
指向要初始化并添加到当前模块[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构的指针。

*pObject*<br/>
指向对象的**此**指针。

### <a name="remarks"></a>备注

初始化`_AtlCreateWndData`结构，用于存储用于引用类实例的`_ATL_WIN_MODULE70`**此**指针，并将其添加到模块结构引用的列表。 由[CAtlWinModule 调用：：添加创建WndData](catlwinmodule-class.md#addcreatewnddata)。

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModule提取创建WndD数据

调用此函数可提取现有 `_AtlCreateWndData` 结构。

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>参数

*pWinModule*<br/>
指向模块[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构的指针。

### <a name="return-value"></a>返回值

返回指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构的指针。

### <a name="remarks"></a>备注

此函数将从模块`_AtlCreateWndData``_ATL_WIN_MODULE70`结构引用的列表中提取现有结构。

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
