---
title: _AtlCreateWndData 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf51197750e9595570a7b011c179c2ed4c7902c3
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880003"
---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData 结构
此结构包含在 atl。 窗口化代码中的类实例数据  
  
## <a name="syntax"></a>语法  
  
```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```  
  
## <a name="members"></a>成员  
 `m_pThis`  
 **这**用于获得在窗口过程中对类实例的指针。  
  
 `m_dwThreadID`  
 当前类实例的线程 ID。  
  
 `m_pNext`  
 指向下一个指针`_AtlCreateWndData`对象。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
## <a name="see-also"></a>请参阅  
 [类和结构](../../atl/reference/atl-classes.md)





