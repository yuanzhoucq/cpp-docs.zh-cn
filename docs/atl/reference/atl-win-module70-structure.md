---
title: "_ATL_WIN_MODULE70 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
ms.sourcegitcommit: 4e393abb2a904a0f5e101efe3d78d0645664397b
ms.openlocfilehash: 383384c8f08b98592f92b5d38850137c1c0c6d54
ms.lasthandoff: 02/24/2017

---
# <a name="atlwinmodule70-structure"></a>_ATL_WIN_MODULE70 结构
使用窗口中的代码 atl。  
  
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
 用于版本控制的结构的大小。  
  
 `m_csWindowCreate`  
 用于序列化对窗口注册代码的访问。 Atl。 在内部使用  
  
 **m_pCreateWndList**  
 用于将 windows 绑定到它们的对象。 Atl。 在内部使用  
  
 **m_rgWindowClassAtoms**  
 用来跟踪窗口类注册的注册，以便可以将其终止时未正确注册。 Atl。 在内部使用  
  
## <a name="remarks"></a>备注  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)定义的 typedef 为`_ATL_WIN_MODULE70`。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
## <a name="see-also"></a>另请参阅  
 [结构](../../atl/reference/atl-structures.md)






