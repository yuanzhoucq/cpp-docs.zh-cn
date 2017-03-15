---
title: "CD2DBrush 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBrush
- afxrendertarget/CD2DBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DBrush class
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
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
ms.openlocfilehash: b9902445fb6e18df20073d132a2117c67e695b25
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dbrush-class"></a>CD2DBrush 类
ID2D1Brush 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DBrush : public CD2DResource;  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DBrush::CD2DBrush](#cd2dbrush)|构造 CD2DBrush 对象。|  
|[CD2DBrush:: ~ CD2DBrush](#_dtorcd2dbrush)|析构函数。 当 D2D 画笔对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DBrush::Attach](#attach)|附加现有的资源的对象的接口|  
|[CD2DBrush::Destroy](#destroy)|销毁 CD2DBrush 对象。 (重写[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DBrush::Detach](#detach)|分离对象中的资源接口|  
|[CD2DBrush::Get](#get)|返回 ID2D1Brush 接口|  
|[CD2DBrush::GetOpacity](#getopacity)|获取此画笔的不透明度|  
|[CD2DBrush::GetTransform](#gettransform)|获取当前呈现器目标的转换|  
|[CD2DBrush::IsValid](#isvalid)|检查资源的有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DBrush::SetOpacity](#setopacity)|设置此画笔的不透明度|  
|[CD2DBrush::SetTransform](#settransform)|适用于呈现器目标，替换现有转换指定的转换。 所有后续的绘图操作将在转换后的空间|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DBrush::operator ID2D1Brush *](#operator_id2d1brush_star)|返回 ID2D1Brush 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DBrush::m_pBrush](#m_pbrush)|存储指向 ID2D1Brush 对象的指针。|  
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|画笔属性。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DBrush`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="a-namedtorcd2dbrusha--cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a>CD2DBrush:: ~ CD2DBrush  
 析构函数。 当 D2D 画笔对象被销毁时调用。  
  
```  
virtual ~CD2DBrush();
```  
  
##  <a name="a-nameattacha--cd2dbrushattach"></a><a name="attach"></a>CD2DBrush::Attach  
 附加现有的资源的对象的接口  
  
```  
void Attach(ID2D1Brush* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 现有资源的接口。 不能为 NULL  
  
##  <a name="a-namecd2dbrusha--cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a>CD2DBrush::CD2DBrush  
 构造 CD2DBrush 对象。  
  
```  
CD2DBrush(
    CRenderTarget* pParentTarget,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pParentTarget`  
 指向该呈现器目标的指针。  
  
 `pBrushProperties`  
 一个指向不透明度和画笔的转换。  
  
 `bAutoDestroy`  
 指示所有者 (pParentTarget) 将销毁该对象。  
  
##  <a name="a-namedestroya--cd2dbrushdestroy"></a><a name="destroy"></a>CD2DBrush::Destroy  
 销毁 CD2DBrush 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="a-namedetacha--cd2dbrushdetach"></a><a name="detach"></a>CD2DBrush::Detach  
 分离对象中的资源接口  
  
```  
ID2D1Brush* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向已分离的资源接口指针。  
  
##  <a name="a-namegeta--cd2dbrushget"></a><a name="get"></a>CD2DBrush::Get  
 返回 ID2D1Brush 接口  
  
```  
ID2D1Brush* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Brush 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="a-namegetopacitya--cd2dbrushgetopacity"></a><a name="getopacity"></a>CD2DBrush::GetOpacity  
 获取此画笔的不透明度  
  
```  
FLOAT GetOpacity() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个介于 0 和 1，该值指示画笔的不透明度之间的值。 此值是常数乘数，可线性扩展由画笔填充的所有像素的 alpha 值。 不透明度值限制为 0 到 1 范围内之前相乘在一起  
  
##  <a name="a-namegettransforma--cd2dbrushgettransform"></a><a name="gettransform"></a>CD2DBrush::GetTransform  
 获取当前呈现器目标的转换  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;  
```  
  
### <a name="parameters"></a>参数  
 `transform`  
 当此方法返回时，包含当前呈现器目标的转换。 此参数未经初始化即被传递  
  
##  <a name="a-nameisvalida--cd2dbrushisvalid"></a><a name="isvalid"></a>CD2DBrush::IsValid  
 检查资源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果资源是有效，则为，TRUE否则为 FALSE。  
  
##  <a name="a-namempbrusha--cd2dbrushmpbrush"></a><a name="m_pbrush"></a>CD2DBrush::m_pBrush  
 存储指向 ID2D1Brush 对象的指针。  
  
```  
ID2D1Brush* m_pBrush;  
```  
  
##  <a name="a-namempbrushpropertiesa--cd2dbrushmpbrushproperties"></a><a name="m_pbrushproperties"></a>CD2DBrush::m_pBrushProperties  
 画笔属性。  
  
```  
CD2DBrushProperties* m_pBrushProperties;  
```  
  
##  <a name="a-nameoperatorid2d1brushstara--cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a>CD2DBrush::operator ID2D1Brush *  
 返回 ID2D1Brush 接口  
  
```  
operator ID2D1Brush*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Brush 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="a-namesetopacitya--cd2dbrushsetopacity"></a><a name="setopacity"></a>CD2DBrush::SetOpacity  
 设置此画笔的不透明度  
  
```  
void SetOpacity(FLOAT opacity);
```  
  
### <a name="parameters"></a>参数  
 `opacity`  
 一个介于 0 和 1，该值指示画笔的不透明度之间的值。 此值是常数乘数，可线性扩展由画笔填充的所有像素的 alpha 值。 不透明度值限制为 0 到 1 范围内之前相乘在一起  
  
##  <a name="a-namesettransforma--cd2dbrushsettransform"></a><a name="settransform"></a>CD2DBrush::SetTransform  
 适用于呈现器目标，替换现有转换指定的转换。 所有后续的绘图操作将在转换后的空间  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>参数  
 `transform`  
 要将应用于呈现器目标的转换  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

