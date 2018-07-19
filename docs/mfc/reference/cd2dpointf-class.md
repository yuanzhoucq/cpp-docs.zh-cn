---
title: CD2DPointF 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e23dbce668234fecc3162d52e0bbea6fb05a7b06
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957268"
---
# <a name="cd2dpointf-class"></a>CD2DPointF 类
`D2D1_POINT_2F`的包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DPointF : public D2D1_POINT_2F;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DPointF::CD2DPointF](#cd2dpointf)|已重载。 构造`CD2DPointF`对象`D2D1_POINT_2F`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DPointF::operator CPoint](#operator_cpoint)|将转换`CD2DPointF`到`CPoint`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `D2D1_POINT_2F`  
  
 `CD2DPointF`  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF  
 构造 CD2DPointF 对象从 CPoint 对象。  
  
```  
CD2DPointF(const CPoint& pt);    
CD2DPointF(const D2D1_POINT_2F& pt);    
CD2DPointF(const D2D1_POINT_2F* pt); 
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```  
  
### <a name="parameters"></a>参数  
 *pt*  
 源点  
  
 *fX*  
 源 X  
  
 *财年*  
 源 Y  
  
##  <a name="operator_cpoint"></a>  CD2DPointF::operator CPoint  
 将 CD2DPointF 转换 CPoint 对象。  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>返回值  
 D2D 点的当前值。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
