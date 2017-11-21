---
title: "设备上下文全局函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlwin/ATL::AtlCreateTargetDC
dev_langs: C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d2560043bc97c384846696b76d8e38b459ae4a34
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="device-context-global-functions"></a>设备上下文全局函数
此函数创建对给定的设备的设备上下文。  
  
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
 [in]存在的句柄的设备上下文，或**NULL**。  
  
 `ptd`  
 [in]指向的指针**DVTARGETDEVICE**结构，其中包含有关目标设备的信息。  
  
### <a name="return-value"></a>返回值  
 中指定的设备的设备上下文中返回的句柄**DVTARGETDEVICE**。 如果不指定任何设备，则返回默认显示设备的句柄。  
  
### <a name="remarks"></a>备注  
 如果结构为**NULL**和*hdc*是**NULL**，创建默认的显示设备的设备上下文。  
  
 如果*hdc*不**NULL**和`ptd`是**NULL**，该函数将返回现有*hdc*。  

## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
   
## <a name="see-also"></a>另请参阅  
 [函数](../../atl/reference/atl-functions.md)
