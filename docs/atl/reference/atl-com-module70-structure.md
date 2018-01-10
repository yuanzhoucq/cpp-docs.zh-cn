---
title: "_ATL_COM_MODULE70 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs: C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f5d1e1d2716c5ab97c2b805a943ffe4587341dc4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atlcommodule70-structure"></a>_ATL_COM_MODULE70 结构
由 COM 相关的代码在 atl。  
  
## <a name="syntax"></a>语法  
  
```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```  
  
## <a name="members"></a>成员  
 `cbSize`  
 结构，用于版本控制的大小。  
  
 `m_hInstTypeLib`  
 实例句柄的与此模块的类型库。  
  
 **m_ppAutoObjMapFirst**  
 指示为此模块对象映射条目的开始的数组元素的地址。  
  
 **m_ppAutoObjMapLast**  
 数组元素，该值指示此模块对象映射条目的结束地址。  
  
 `m_csObjMap`  
 要序列化到对象映射项的访问的关键部分。 Atl。 在内部使用  
  
## <a name="remarks"></a>备注  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)指的 typedef `_ATL_COM_MODULE70`。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
## <a name="see-also"></a>请参阅  
 [结构](../../atl/reference/atl-structures.md)





