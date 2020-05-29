---
title: CD2DGradientBrush 类
ms.date: 03/27/2019
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
ms.openlocfilehash: 861bc32382737bd6482a3d51eb8470bf834e8508
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369221"
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush 类

CD2D线性渐变画笔和 CD2DRadial 梯度画笔类的基类。

## <a name="syntax"></a>语法

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D 梯度画笔：：CD2D 梯度画笔](#cd2dgradientbrush)|构造 CD2D 梯度画笔对象。|
|[CD2D 梯度画笔：*CD2D 梯度画笔](#_dtorcd2dgradientbrush)|析构函数。 销毁 D2D 渐变画笔对象时调用。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CD2D梯度画笔：:D](#destroy)|销毁 CD2D 梯度画笔对象。 （覆盖[CD2DBrush：:Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).）|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D 梯度画笔：：m_arGradientStops](#m_argradientstops)|D2D1_GRADIENT_STOP结构的数组。|
|[CD2D 梯度画笔：：m_colorInterpolationGamma](#m_colorinterpolationgamma)|在渐变停止之间执行颜色插值的空间。|
|[CD2D 梯度画笔：：m_extendMode](#m_extendmode)|渐变在 [0，1] 规范化范围之外的行为。|
|[CD2D 梯度画笔：：m_pGradientStops](#m_pgradientstops)|指向D2D1_GRADIENT_STOP结构数组的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="_dtorcd2dgradientbrush"></a>CD2D 梯度画笔：*CD2D 梯度画笔

析构函数。 销毁 D2D 渐变画笔对象时调用。

```
virtual ~CD2DGradientBrush();
```

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="cd2dgradientbrush"></a>CD2D 梯度画笔：：CD2D 梯度画笔

构造 CD2D 梯度画笔对象。

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

*p 父目标*<br/>
指向渲染目标的指针。

*梯度停止*<br/>
指向D2D1_GRADIENT_STOP结构数组的指针。

*梯度停止计数*<br/>
大于或等于 1 的值，用于指定渐变停止数组中的渐变停止数。

*颜色插值伽马*<br/>
在渐变停止之间执行颜色插值的空间。

*扩展模式*<br/>
渐变在 [0，1] 规范化范围之外的行为。

*pBrush 属性*<br/>
指向画笔的不一用性和变换的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dgradientbrushdestroy"></a><a name="destroy"></a>CD2D梯度画笔：:D

销毁 CD2D 梯度画笔对象。

```
virtual void Destroy();
```

## <a name="cd2dgradientbrushm_argradientstops"></a><a name="m_argradientstops"></a>CD2D 梯度画笔：：m_arGradientStops

D2D1_GRADIENT_STOP结构的数组。

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

## <a name="cd2dgradientbrushm_colorinterpolationgamma"></a><a name="m_colorinterpolationgamma"></a>CD2D 梯度画笔：：m_colorInterpolationGamma

在渐变停止之间执行颜色插值的空间。

```
D2D1_GAMMA m_colorInterpolationGamma;
```

## <a name="cd2dgradientbrushm_extendmode"></a><a name="m_extendmode"></a>CD2D 梯度画笔：：m_extendMode

渐变在 [0，1] 规范化范围之外的行为。

```
D2D1_EXTEND_MODE m_extendMode;
```

## <a name="cd2dgradientbrushm_pgradientstops"></a><a name="m_pgradientstops"></a>CD2D 梯度画笔：：m_pGradientStops

指向D2D1_GRADIENT_STOP结构数组的指针。

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
