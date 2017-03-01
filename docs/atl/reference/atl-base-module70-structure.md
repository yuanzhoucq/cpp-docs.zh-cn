---
title: "_ATL_BASE_MODULE70 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
caps.latest.revision: 15
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
translationtype: Machine Translation
ms.sourcegitcommit: 347e7bf7cd9173fb2815f44fc052ec23ab4055a6
ms.openlocfilehash: 7456d441d7b3fb74f404f29c893c492feab10ed9
ms.lasthandoff: 02/24/2017

---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 结构
使用的任何项目都使用 atl。  
  
## <a name="syntax"></a>语法  
  
```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```  
  
## <a name="members"></a>成员  
 `cbSize`  
 用于版本控制的结构的大小。  
  
 `m_hInst`  
 **HInstance**此模块 （exe 或 dll）。  
  
 `m_hInstResource`  
 默认实例的资源句柄。  
  
 **m_bNT5orWin98**  
 操作系统版本信息。 Atl。 在内部使用  
  
 **dwAtlBuildVer**  
 存储的版本 atl。 当前 0x0700。  
  
 **pguidVer**  
 ATL 的内部 GUID。  
  
 **m_csResource**  
 用于同步对**m_rgResourceInstance**数组。 Atl。 在内部使用  
  
 **m_rgResourceInstance**  
 用于搜索 ATL 的感知的所有资源实例中的资源的数组。 Atl。 在内部使用  
  
## <a name="remarks"></a>备注  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)定义的 typedef 为`_ATL_BASE_MODULE70`。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcore.h  
  
## <a name="see-also"></a>另请参阅  
 [结构](../../atl/reference/atl-structures.md)






