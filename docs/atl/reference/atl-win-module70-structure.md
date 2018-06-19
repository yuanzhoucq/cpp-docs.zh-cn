---
title: _ATL_WIN_MODULE70 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 587b115c428b0d82183abbec9f712ff06ea448f4
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256075"
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
  
## <a name="see-also"></a>请参阅  
 [类和结构](../../atl/reference/atl-classes.md)





