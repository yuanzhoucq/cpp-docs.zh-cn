---
title: WinModule Global 函数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 1a929fd0f583150e84ce5b1efa7e896bc16e4247
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229930"
---
# <a name="winmodule-global-functions"></a>WinModule Global 函数

这些函数提供对 `_AtlCreateWndData` 结构操作的支持。

> [!IMPORTANT]
> 下表中列出的函数不能用于在 Windows 运行时中执行的应用程序。

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函数用于初始化和添加`_AtlCreateWndData` 结构。|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|调用此函数可提取现有 `_AtlCreateWndData` 结构。|

## <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData

此函数用于初始化和添加`_AtlCreateWndData` 结构。

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>参数

*pWinModule*<br/>
指向模块的[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构的指针。

*pData*<br/>
一个指针，指向要初始化并添加到当前模块的[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构。

*pObject*<br/>
指向对象的指针的指针 **`this`** 。

### <a name="remarks"></a>备注

初始化一个 `_AtlCreateWndData` 结构，该结构用于存储 **`this`** 用于引用类实例的指针，并将其添加到模块结构所引用的列表 `_ATL_WIN_MODULE70` 。 由[CAtlWinModule：： AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)调用。

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData

调用此函数可提取现有 `_AtlCreateWndData` 结构。

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>参数

*pWinModule*<br/>
指向模块的[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构的指针。

### <a name="return-value"></a>返回值

返回指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构的指针。

### <a name="remarks"></a>备注

此函数将 `_AtlCreateWndData` 从模块结构引用的列表中提取现有结构 `_ATL_WIN_MODULE70` 。

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)
