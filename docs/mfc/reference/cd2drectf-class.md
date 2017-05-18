---
title: "CD2DRectF 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectF class
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5bca2dcce32679083e5917d855f711984989a489
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CD2DRectF::IsNull](#isnull)|返回`boolean`值，该值指示表达式是否包含无效数据 ( `null`)。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DRectF::operator CRect](#operator_crect)|将转换`CD2DRectF`到`CRect`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `D2D1_RECT_F`  
  
 `CD2DRectF`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="cd2drectf"></a>CD2DRectF::CD2DRectF  
 构造 CD2DRectF 对象从 CRect 对象。  
  
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
 `rect`  
 源矩形  
  
 `fLeft`  
 源左的坐标  
  
 `fTop`  
 源上坐标  
  
 `fRight`  
 源右边坐标  
  
 `fBottom`  
 源底部坐标  
  
##  <a name="isnull"></a>CD2DRectF::IsNull  
 返回一个布尔值，该值指示表达式是否包含无效数据 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>返回值  
 矩形的顶部、 左边框、 下、 和正确的值完全等于 0; 如果为 TRUE否则为 FALSE。  
  
##  <a name="operator_crect"></a>CD2DRectF::operator CRect  
 将 CD2DRectF 转换成 CRect 对象。  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>返回值  
 D2D 矩形的当前值。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

