---
title: "_ATL_MODULE70 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
caps.latest.revision: 16
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
ms.sourcegitcommit: 4e393abb2a904a0f5e101efe3d78d0645664397b
ms.openlocfilehash: ea1d87d3d500fc08f3da16de6820ca003e899419
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="atlmodule70-structure"></a>_ATL_MODULE70 结构
包含每个 ATL 模块使用的数据。  
  
## <a name="syntax"></a>语法  
  
```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```  
  
## <a name="members"></a>成员  
 `cbSize`  
 用于版本控制的结构的大小。  
  
 `m_nLockCnt`  
 引用计数以确定模块应保留多长时间保持活动状态。  
  
 **m_pTermFuncs**  
 已注册在 ATL 关闭时要调用的跟踪功能。  
  
 **m_csStaticDataInitAndTypeInfo**  
 用于协调对在多线程情况下的内部数据的访问。  
  
## <a name="remarks"></a>备注  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)定义的 typedef 为`_ATL_MODULE70`。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
## <a name="see-also"></a>另请参阅  
 [结构](../../atl/reference/atl-structures.md)








