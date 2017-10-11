---
title: "_ATL_BASE_MODULE70 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 1e824c2b85e7f80ad93a1f154be7f2e680bd00a9
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 结构
使用 atl。 任何项目使用  
  
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
 结构，用于版本控制的大小。  
  
 `m_hInst`  
 **HInstance**为此模块 （exe 或 dll）。  
  
 `m_hInstResource`  
 默认实例资源句柄。  
  
 **m_bNT5orWin98**  
 操作系统版本信息。 Atl。 在内部使用  
  
 **dwAtlBuildVer**  
 将存储的新版 atl。 当前 0x0700。  
  
 **pguidVer**  
 ATL 的内部 GUID。  
  
 **m_csResource**  
 使用对访问进行同步**m_rgResourceInstance**数组。 Atl。 在内部使用  
  
 **m_rgResourceInstance**  
 用于搜索 ATL 的感知的所有资源实例中的资源的数组。 Atl。 在内部使用  
  
## <a name="remarks"></a>备注  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)指的 typedef `_ATL_BASE_MODULE70`。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcore.h  
  
## <a name="see-also"></a>另请参阅  
 [结构](../../atl/reference/atl-structures.md)






