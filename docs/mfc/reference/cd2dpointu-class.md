---
title: "CD2DPointU 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f5af7ab3327a7c3d2f1afc31ad8cc2bde144eeb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dpointu-class"></a>CD2DPointU 类
`D2D1_POINT_2U`的包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DPointU : public D2D1_POINT_2U;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DPointU::CD2DPointU](#cd2dpointu)|已重载。 构造`CD2DPointU`从对象`D2D1_POINT_2U`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DPointU::operator CPoint](#operator_cpoint)|将转换`CD2DPointU`到`CPoint`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `D2D1_POINT_2U`  
  
 `CD2DPointU`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxrendertarget.h  
  
##  <a name="cd2dpointu"></a>CD2DPointU::CD2DPointU  
 构造 CD2DPointU 对象从 CPoint 对象。  
  
```  
CD2DPointU(const CPoint& pt);  
CD2DPointU(const D2D1_POINT_2U& pt);  
  CD2DPointU(const D2D1_POINT_2U* pt);  
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 源点  
  
 `uX`  
 源 X  
  
 `uY`  
 源 Y  
  
##  <a name="operator_cpoint"></a>CD2DPointU::operator CPoint  
 将 CD2DPointU 转换 CPoint 对象。  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>返回值  
 D2D 点的当前值。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
