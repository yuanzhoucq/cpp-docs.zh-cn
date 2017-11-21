---
title: "对象状态宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs: C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc74d545388199eab2aca63ecdea1fdd62a9ef23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="object-status-macros"></a>对象状态宏
此宏设置属于 ActiveX 控件的标志。  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|ATL ActiveX 控件中用于设置**OLEMISC**标志。|  

## <a name="requirements"></a>要求  
 **标头：** atlcom.h  

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS  
 使用 ATL ActiveX 控件中设置 OLEMISC 标志。  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>参数  
 *miscstatus*  
 所有适用 OLEMISC 标志。  
  
### <a name="remarks"></a>备注  
 使用此宏设置 ActiveX 控件 OLEMISC 标志。 请参阅[IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521)有关详细信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)
