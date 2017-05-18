---
title: "对象状态宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 433a816b19690f22f482f26f6ab70c73ed102673
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="object-status-macros"></a>对象状态宏
此宏设置属于 ActiveX 控件的标志。  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|ATL ActiveX 控件中用于设置**OLEMISC**标志。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS  
 ATL ActiveX 控件中用于设置 OLEMISC 标志。  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>参数  
 *miscstatus*  
 所有适用的 OLEMISC 标志。  
  
### <a name="remarks"></a>备注  
 使用此宏设置为 ActiveX 控件的 OLEMISC 标志。 请参阅[IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521)的更多详细信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&124;](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

