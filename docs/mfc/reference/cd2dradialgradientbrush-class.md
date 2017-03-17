---
title: "CD2DRadialGradientBrush 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DRadialGradientBrush class
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8b3fd7f468745567969ba1f7e9d6871a9060582b
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush 类
ID2D1RadialGradientBrush 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DRadialGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|构造 CD2DLinearGradientBrush 对象。|  
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|析构函数。 当 D2D 径向渐变画笔对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::Attach](#attach)|附加现有的资源的对象的接口|  
|[CD2DRadialGradientBrush::Create](#create)|创建 CD2DRadialGradientBrush。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DRadialGradientBrush::Destroy](#destroy)|销毁 CD2DRadialGradientBrush 对象。 (重写[CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy)。)|  
|[CD2DRadialGradientBrush::Detach](#detach)|分离对象中的资源接口|  
|[CD2DRadialGradientBrush::Get](#get)|返回 ID2D1RadialGradientBrush 接口|  
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|检索渐变椭圆的中心|  
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|检索该渐变原点相对于渐变椭圆中心的偏移量|  
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|检索的渐变的椭圆的 x 半径|  
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|检索的渐变椭圆 y 半径|  
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|画笔的坐标空间中指定的渐变的椭圆的中心|  
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|指定渐变原点相对于渐变椭圆中心的偏移量|  
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|指定渐变椭圆，x 轴半径画笔的坐标空间中|  
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|指定渐变椭圆，y 轴半径画笔的坐标空间中|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|返回 ID2D1RadialGradientBrush 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|指向 ID2D1RadialGradientBrush 的指针。|  
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|中心、 渐变原点偏移量和 x 轴半径和 y 轴半径画笔的渐变。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DRadialGradientBrush`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush  
 析构函数。 当 D2D 径向渐变画笔对象被销毁时调用。  
  
```  
virtual ~CD2DRadialGradientBrush();
```  
  
##  <a name="attach"></a>CD2DRadialGradientBrush::Attach  
 附加现有的资源的对象的接口  
  
```  
void Attach(ID2D1RadialGradientBrush* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 现有资源的接口。 不能为 NULL  
  
##  <a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush  
 构造 CD2DLinearGradientBrush 对象。  
  
```  
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,  
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
  
 `RadialGradientBrushProperties`  
 中心、 渐变原点偏移量和 x 轴半径和 y 轴半径画笔的渐变。  
  
 `colorInterpolationGamma`  
 在哪种颜色执行内插的渐变停止点之间的空间。  
  
 `extendMode`  
 [0，1] 的规范化范围之外的渐变的行为。  
  
 `pBrushProperties`  
 一个指向不透明度和画笔的转换。  
  
 `bAutoDestroy`  
 指示所有者 (pParentTarget) 将销毁该对象。  
  
##  <a name="create"></a>CD2DRadialGradientBrush::Create  
 创建 CD2DRadialGradientBrush。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>参数  
 `pRenderTarget`  
 指向该呈现器目标的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="destroy"></a>CD2DRadialGradientBrush::Destroy  
 销毁 CD2DRadialGradientBrush 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DRadialGradientBrush::Detach  
 分离对象中的资源接口  
  
```  
ID2D1RadialGradientBrush* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向已分离的资源接口指针。  
  
##  <a name="get"></a>CD2DRadialGradientBrush::Get  
 返回 ID2D1RadialGradientBrush 接口  
  
```  
ID2D1RadialGradientBrush* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1RadialGradientBrush 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter  
 检索渐变椭圆的中心  
  
```  
CD2DPointF GetCenter() const;  
```  
  
### <a name="return-value"></a>返回值  
 渐变的椭圆的中心。 此值表示画笔的坐标空间  
  
##  <a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset  
 检索该渐变原点相对于渐变椭圆中心的偏移量  
  
```  
CD2DPointF GetGradientOriginOffset() const;  
```  
  
### <a name="return-value"></a>返回值  
 偏移量从渐变椭圆中心渐变的原点。 此值表示画笔的坐标空间  
  
##  <a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX  
 检索的渐变的椭圆的 x 半径  
  
```  
FLOAT GetRadiusX() const;  
```  
  
### <a name="return-value"></a>返回值  
 渐变椭圆 x 半径。 此值表示画笔的坐标空间  
  
##  <a name="getradiusy"></a>CD2DRadialGradientBrush::GetRadiusY  
 检索的渐变椭圆 y 半径  
  
```  
FLOAT GetRadiusY() const;  
```  
  
### <a name="return-value"></a>返回值  
 渐变椭圆 y 半径。 此值表示画笔的坐标空间  
  
##  <a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush  
 指向 ID2D1RadialGradientBrush 的指针。  
  
```  
ID2D1RadialGradientBrush* m_pRadialGradientBrush;  
```  
  
##  <a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties  
 中心、 渐变原点偏移量和 x 轴半径和 y 轴半径画笔的渐变。  
  
```  
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;  
```  
  
##  <a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *  
 返回 ID2D1RadialGradientBrush 接口  
  
```  
operator ID2D1RadialGradientBrush*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1RadialGradientBrush 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter  
 画笔的坐标空间中指定的渐变的椭圆的中心  
  
```  
void SetCenter(CD2DPointF point);
```  
  
### <a name="parameters"></a>参数  
 `point`  
 渐变椭圆，画笔的坐标空间中的中心  
  
##  <a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset  
 指定渐变原点相对于渐变椭圆中心的偏移量  
  
```  
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```  
  
### <a name="parameters"></a>参数  
 `gradientOriginOffset`  
 渐变的渐变的椭圆的中心从原点的偏移量  
  
##  <a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX  
 指定渐变椭圆，x 轴半径画笔的坐标空间中  
  
```  
void SetRadiusX(FLOAT radiusX);
```  
  
### <a name="parameters"></a>参数  
 `radiusX`  
 渐变椭圆 x 半径。 此值是画笔的坐标空间  
  
##  <a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusY  
 指定渐变椭圆，y 轴半径画笔的坐标空间中  
  
```  
void SetRadiusY(FLOAT radiusY);
```  
  
### <a name="parameters"></a>参数  
 `radiusY`  
 渐变椭圆 y 半径。 此值是画笔的坐标空间  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

