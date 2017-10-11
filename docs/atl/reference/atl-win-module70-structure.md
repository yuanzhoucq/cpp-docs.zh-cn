---
title: "_ATL_WIN_MODULE70 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 7f521b418b7d179eb506a5e9df2887addec059ef
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="atlwinmodule70-structure"></a>_ATL_WIN_MODULE70 结构
使用窗口化代码在 atl。  
  
## <a name="syntax"></a>语法  
  
```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize; 
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```  
  
## <a name="members"></a>成员  
 `cbSize`  
 结构，用于版本控制的大小。  
  
 `m_csWindowCreate`  
 用于序列化对窗口注册代码的访问。 Atl。 在内部使用  
  
 **m_pCreateWndList**  
 用于将 windows 绑定到它们的对象。 Atl。 在内部使用  
  
 **m_rgWindowClassAtoms**  
 用于跟踪窗口类注册，以便它们可以在终止正确注销。 Atl。 在内部使用  
  
## <a name="remarks"></a>备注  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)指的 typedef `_ATL_WIN_MODULE70`。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
## <a name="see-also"></a>另请参阅  
 [结构](../../atl/reference/atl-structures.md)






