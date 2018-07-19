---
title: 对象状态宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3657e7076bf67a5a3870d7d127cc150f976ecde
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883653"
---
# <a name="object-status-macros"></a>对象状态宏
此宏设置属于 ActiveX 控件的标志。  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|ATL ActiveX 控件中用于设置 OLEMISC 标志。|  

## <a name="requirements"></a>要求  
 **标头：** atlcom.h  

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS  
 ATL ActiveX 控件中用于设置 OLEMISC 标志。  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>参数  
 *miscstatus*  
 所有适用 OLEMISC 标志。  
  
### <a name="remarks"></a>备注  
 使用此宏设置 ActiveX 控件的 OLEMISC 标志。 请参阅[IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521)的更多详细信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
