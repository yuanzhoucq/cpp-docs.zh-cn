---
title: "CD2DLinearGradientBrush 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CD2DLinearGradientBrush
- CD2DLinearGradientBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DLinearGradientBrush class
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
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
ms.openlocfilehash: dd288478a751d921cc4d9fcd9433e391275cee66
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush 类
ID2D1LinearGradientBrush 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DLinearGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|构造 CD2DLinearGradientBrush 对象。|  
|[CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|析构函数。 当 D2D 线性渐变画笔对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::Attach](#attach)|附加现有的资源的对象的接口|  
|[CD2DLinearGradientBrush::Create](#create)|创建 CD2DLinearGradientBrush。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DLinearGradientBrush::Destroy](#destroy)|销毁 CD2DLinearGradientBrush 对象。 (重写[CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy)。)|  
|[CD2DLinearGradientBrush::Detach](#detach)|分离对象中的资源接口|  
|[CD2DLinearGradientBrush::Get](#get)|返回 ID2D1LinearGradientBrush 接口|  
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|检索线性渐变的终止坐标|  
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|检索线性渐变的起始坐标|  
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|集的线性渐变画笔的坐标空间中的终止坐标|  
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|集的线性渐变画笔的坐标空间中的起始坐标|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|返回 ID2D1LinearGradientBrush 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|起点和终点的渐变。|  
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|指向 ID2D1LinearGradientBrush 的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DLinearGradientBrush`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="a-namedtorcd2dlineargradientbrusha--cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush  
 析构函数。 当 D2D 线性渐变画笔对象被销毁时调用。  
  
```  
virtual ~CD2DLinearGradientBrush();
```  
  
##  <a name="a-nameattacha--cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2DLinearGradientBrush::Attach  
 附加现有的资源的对象的接口  
  
```  
void Attach(ID2D1LinearGradientBrush* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 现有资源的接口。 不能为 NULL  
  
##  <a name="a-namecd2dlineargradientbrusha--cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush  
 构造 CD2DLinearGradientBrush 对象。  
  
```  
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,  
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
  
 `LinearGradientBrushProperties`  
 起点和终点的渐变。  
  
 `colorInterpolationGamma`  
 在哪种颜色执行内插的渐变停止点之间的空间。  
  
 `extendMode`  
 [0，1] 的规范化范围之外的渐变的行为。  
  
 `pBrushProperties`  
 一个指向不透明度和画笔的转换。  
  
 `bAutoDestroy`  
 指示所有者 (pParentTarget) 将销毁该对象。  
  
##  <a name="a-namecreatea--cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2DLinearGradientBrush::Create  
 创建 CD2DLinearGradientBrush。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>参数  
 `pRenderTarget`  
 指向该呈现器目标的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="a-namedestroya--cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2DLinearGradientBrush::Destroy  
 销毁 CD2DLinearGradientBrush 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="a-namedetacha--cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2DLinearGradientBrush::Detach  
 分离对象中的资源接口  
  
```  
ID2D1LinearGradientBrush* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向已分离的资源接口指针。  
  
##  <a name="a-namegeta--cd2dlineargradientbrushget"></a><a name="get"></a>CD2DLinearGradientBrush::Get  
 返回 ID2D1LinearGradientBrush 接口  
  
```  
ID2D1LinearGradientBrush* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1LinearGradientBrush 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="a-namegetendpointa--cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint  
 检索线性渐变的终止坐标  
  
```  
CD2DPointF GetEndPoint() const;  
```  
  
### <a name="return-value"></a>返回值  
 线性渐变画笔的坐标空间中的二维终止坐标  
  
##  <a name="a-namegetstartpointa--cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint  
 检索线性渐变的起始坐标  
  
```  
CD2DPointF GetStartPoint() const;  
```  
  
### <a name="return-value"></a>返回值  
 线性渐变画笔的坐标空间中二维起始坐标  
  
##  <a name="a-namemlineargradientbrushpropertiesa--cd2dlineargradientbrushmlineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties  
 起点和终点的渐变。  
  
```  
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;  
```  
  
##  <a name="a-namemplineargradientbrusha--cd2dlineargradientbrushmplineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush  
 指向 ID2D1LinearGradientBrush 的指针。  
  
```  
ID2D1LinearGradientBrush* m_pLinearGradientBrush;  
```  
  
##  <a name="a-nameoperatorid2d1lineargradientbrushstara--cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *  
 返回 ID2D1LinearGradientBrush 接口  
  
```  
operator ID2D1LinearGradientBrush*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1LinearGradientBrush 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="a-namesetendpointa--cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint  
 集的线性渐变画笔的坐标空间中的终止坐标  
  
```  
void SetEndPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>参数  
 `point`  
 线性渐变画笔的坐标空间中的二维终止坐标  
  
##  <a name="a-namesetstartpointa--cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint  
 集的线性渐变画笔的坐标空间中的起始坐标  
  
```  
void SetStartPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>参数  
 `point`  
 线性渐变画笔的坐标空间中二维起始坐标  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

