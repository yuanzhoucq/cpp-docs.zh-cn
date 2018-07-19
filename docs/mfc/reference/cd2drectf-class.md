---
title: CD2DRectF 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f96adf519eb710d412465a9db4cbd7313f91f41
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338267"
---
# <a name="cd2drectf-class"></a>CD2DRectF 类
`D2D1_RECT_F`的包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DRectF::CD2DRectF](#cd2drectf)|已重载。 构造`CD2DRectF`对象从`D2D1_RECT_F`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DRectF::IsNull](#isnull)|返回**布尔**值，该值指示表达式是否包含任何有效的数据 (NULL)。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DRectF::operator CRect](#operator_crect)|将转换`CD2DRectF`到`CRect`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `D2D1_RECT_F`  
  
 `CD2DRectF`  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF  
 构造 CRect 对象从一个 CD2DRectF 对象。  
  
```  
CD2DRectF(const CRect& rect);  
CD2DRectF(const D2D1_RECT_F& rect);  
  CD2DRectF(const D2D1_RECT_F* rect);

 
CD2DRectF(
    FLOAT fLeft = 0.,  
    FLOAT fTop = 0.,  
    FLOAT fRight = 0.,  
    FLOAT fBottom = 0.);
```  
  
### <a name="parameters"></a>参数  
 *rect*  
 源矩形  
  
 *fLeft*  
 源左边缘坐标  
  
 *fTop*  
 源上边缘坐标  
  
 *了恐惧*  
 源角坐标  
  
 *fBottom*  
 源下边缘坐标  
  
##  <a name="isnull"></a>  CD2DRectF::IsNull  
 返回一个布尔值，该值指示表达式是否包含任何有效的数据 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>返回值  
 矩形的上、 左、 下、 和正确的值均相等，则为 0; 如果为 TRUE否则为 FALSE。  
  
##  <a name="operator_crect"></a>  CD2DRectF::operator CRect  
 将 CD2DRectF 转换为 CRect 对象。  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>返回值  
 D2D 矩形的当前值。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
