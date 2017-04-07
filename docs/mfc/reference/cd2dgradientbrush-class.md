---
title: "CD2DGradientBrush 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
dev_langs:
- C++
helpviewer_keywords:
- CD2DGradientBrush class
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
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
translationtype: Machine Translation
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 0b0a692ef2b5194daf7b38eed9ebe3b2f4eda448
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush 类
CD2DLinearGradientBrush 和 CD2DRadialGradientBrush 类的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DGradientBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|构造 CD2DGradientBrush 对象。|  
|[CD2DGradientBrush:: ~ CD2DGradientBrush](#cd2dgradientbrush__~cd2dgradientbrush)|析构函数。 当 D2D 渐变画笔对象被销毁时调用。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DGradientBrush::Destroy](#destroy)|销毁 CD2DGradientBrush 对象。 (重写[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy)。)|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|D2D1_GRADIENT_STOP 结构的数组。|  
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|在哪种颜色执行内插的渐变停止点之间的空间。|  
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|[0，1] 的规范化范围之外的渐变的行为。|  
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|指向一个 D2D1_GRADIENT_STOP 结构数组的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DGradientBrush`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="_dtorcd2dgradientbrush"></a>CD2DGradientBrush:: ~ CD2DGradientBrush  
 析构函数。 当 D2D 渐变画笔对象被销毁时调用。  
  
```  
virtual ~CD2DGradientBrush();
```  
  
##  <a name="cd2dgradientbrush"></a>CD2DGradientBrush::CD2DGradientBrush  
 构造 CD2DGradientBrush 对象。  
  
```  
CD2DGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,  
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pParentTarget`  
 指向该呈现器目标的指针。  
  
 `gradientStops`  
 指向一个 D2D1_GRADIENT_STOP 结构数组的指针。  
  
 `gradientStopsCount`  
 一个值大于或等于 1，gradientStops 数组中指定的渐变停止点的数目。  
  
 `colorInterpolationGamma`  
 在哪种颜色执行内插的渐变停止点之间的空间。  
  
 `extendMode`  
 [0，1] 的规范化范围之外的渐变的行为。  
  
 `pBrushProperties`  
 一个指向不透明度和画笔的转换。  
  
 `bAutoDestroy`  
 指示所有者 (pParentTarget) 将销毁该对象。  
  
##  <a name="destroy"></a>CD2DGradientBrush::Destroy  
 销毁 CD2DGradientBrush 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="m_argradientstops"></a>CD2DGradientBrush::m_arGradientStops  
 D2D1_GRADIENT_STOP 结构的数组。  
  
```  
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;  
```  
  
##  <a name="m_colorinterpolationgamma"></a>CD2DGradientBrush::m_colorInterpolationGamma  
 在哪种颜色执行内插的渐变停止点之间的空间。  
  
```  
D2D1_GAMMA m_colorInterpolationGamma;  
```  
  
##  <a name="m_extendmode"></a>CD2DGradientBrush::m_extendMode  
 [0，1] 的规范化范围之外的渐变的行为。  
  
```  
D2D1_EXTEND_MODE m_extendMode;  
```  
  
##  <a name="m_pgradientstops"></a>CD2DGradientBrush::m_pGradientStops  
 指向一个 D2D1_GRADIENT_STOP 结构数组的指针。  
  
```  
ID2D1GradientStopCollection* m_pGradientStops;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

