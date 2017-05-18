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
dev_langs:
- C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: c477f4500bd4fe78f21f04c58b02d1b493f72c01
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="winmodule-global-functions"></a>WinModule 全局函数
这些函数提供了对支持`_AtlCreateWndData`结构操作。  
  
> [!IMPORTANT]
>  下表中列出的函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函数用于初始化和添加`_AtlCreateWndData` 结构。|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|调用此函数可提取现有 `_AtlCreateWndData` 结构。|  

## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
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
 指向模块的指针[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构。  
  
 `pData`  
 指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构要初始化和添加到当前的模块。  
  
 `pObject`  
 指针指向的对象**这**指针。  
  
### <a name="remarks"></a>备注  
 初始化`_AtlCreateWndData`结构，用于存储**这**指针用来引用类的实例，并将其添加到引用的模块的列表`_ATL_WIN_MODULE70`结构。 由调用[CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)。  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData  
 调用此函数可提取现有 `_AtlCreateWndData` 结构。  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>参数  
 `pWinModule`  
 指向模块的指针[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)结构。  
  
### <a name="return-value"></a>返回值  
 返回一个指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 此函数将提取现有`_AtlCreateWndData`从引用的模块的列表结构`_ATL_WIN_MODULE70`结构。  
  
## <a name="see-also"></a>另请参阅  
 [函数](../../atl/reference/atl-functions.md)

