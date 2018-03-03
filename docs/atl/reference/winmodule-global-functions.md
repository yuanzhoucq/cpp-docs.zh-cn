---
title: "WinModule 全局函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs:
- C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 290566c27fa5698c4a00a323a8c2431681b69d88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="winmodule-global-functions"></a>WinModule 全局函数
这些函数都提供支持`_AtlCreateWndData`结构操作。  
  
> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序。  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函数用于初始化和添加`_AtlCreateWndData` 结构。|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|调用此函数可提取现有 `_AtlCreateWndData` 结构。|  

## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  `            
##  <a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData  
 此函数用于初始化和添加`_AtlCreateWndData` 结构。  
   
```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```  
  
### <a name="parameters"></a>参数  
 `pWinModule`  
 指向模块的[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构。  
  
 `pData`  
 指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构来初始化和添加到当前的模块。  
  
 `pObject`  
 指针指向的对象**这**指针。  
  
### <a name="remarks"></a>备注  
 初始化`_AtlCreateWndData`结构，用于存储**这**指针来引用类的实例，并将其添加到引用的模块的列表`_ATL_WIN_MODULE70`结构。 由调用[CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)。  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData  
 调用此函数可提取现有 `_AtlCreateWndData` 结构。  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>参数  
 `pWinModule`  
 指向模块的[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构。  
  
### <a name="return-value"></a>返回值  
 返回一个指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 此函数将提取现有`_AtlCreateWndData`从引用的模块的列表的结构`_ATL_WIN_MODULE70`结构。  
  
## <a name="see-also"></a>请参阅  
 [函数](../../atl/reference/atl-functions.md)
