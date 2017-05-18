---
title: "设备上下文的全局函数 |Microsoft 文档"
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
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
caps.latest.revision: 17
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
ms.openlocfilehash: 8c71781519b965717acbcefab6fe6a183686caef
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="device-context-global-functions"></a>设备上下文的全局函数
此函数创建为给定设备的设备上下文。  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|创建设备上下文。|  
  
##  <a name="atlcreatetargetdc"></a>AtlCreateTargetDC  
 创建设备上下文中指定的设备[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)结构。  
  
```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```  
  
### <a name="parameters"></a>参数  
 *hdc*  
 [in]现有的设备上下文的句柄或**NULL**。  
  
 `ptd`  
 [in]一个指向**DVTARGETDEVICE**结构，其中包含有关目标设备的信息。  
  
### <a name="return-value"></a>返回值  
 中指定的设备的设备上下文中返回的句柄**DVTARGETDEVICE**。 如果未不指定任何设备，返回到默认显示设备的句柄。  
  
### <a name="remarks"></a>备注  
 如果结构**NULL**和*hdc*是**NULL**，创建默认显示设备的设备上下文。  
  
 如果*hdc*不是**NULL**和`ptd`是**NULL**，该函数将返回现有*hdc*。  

## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
   
## <a name="see-also"></a>另请参阅  
 [函数](../../atl/reference/atl-functions.md)

