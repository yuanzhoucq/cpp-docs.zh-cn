---
title: "_ATL_MODULE70 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a759306e4218d36f2a4d250209f67b1d181c483
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
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
 结构，用于版本控制的大小。  
  
 `m_nLockCnt`  
 引用计数以确定多长时间将模块应保持活动状态。  
  
 **m_pTermFuncs**  
 跟踪已注册在 ATL 关闭时要调用的函数。  
  
 **m_csStaticDataInitAndTypeInfo**  
 用于协调对内部数据在多线程情况下的访问。  
  
## <a name="remarks"></a>备注  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)指的 typedef `_ATL_MODULE70`。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
## <a name="see-also"></a>请参阅  
 [结构](../../atl/reference/atl-structures.md)







