---
title: WinModule 全局函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs:
- C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08cfa128ecb598d4960c0d5527e66a9cb81266c2
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752438"
---
# <a name="winmodule-global-functions"></a>WinModule 全局函数

这些函数提供的支持`_AtlCreateWndData`结构操作。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函数用于初始化和添加`_AtlCreateWndData` 结构。|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|调用此函数可提取现有 `_AtlCreateWndData` 结构。|

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="atlwinmoduleaddcreatewnddata"></a>  AtlWinModuleAddCreateWndData

此函数用于初始化和添加`_AtlCreateWndData` 结构。

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>参数

*pWinModule*  
指向模块的指针[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构。

*pData*  
指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构，以初始化，并添加到当前模块。

*pObject*  
指向对象的指针**这**指针。

### <a name="remarks"></a>备注

初始化`_AtlCreateWndData`结构，用于存储**这**指针用于指代类的实例，并将其添加到引用的模块的列表`_ATL_WIN_MODULE70`结构。 调用[CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)。

##  <a name="atlwinmoduleextractcreatewnddata"></a>  AtlWinModuleExtractCreateWndData

调用此函数可提取现有 `_AtlCreateWndData` 结构。

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>参数

*pWinModule*  
指向模块的指针[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构。

### <a name="return-value"></a>返回值

返回一个指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构。

### <a name="remarks"></a>备注

此函数将提取的现有`_AtlCreateWndData`从列表中引用的模块的结构`_ATL_WIN_MODULE70`结构。

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)
