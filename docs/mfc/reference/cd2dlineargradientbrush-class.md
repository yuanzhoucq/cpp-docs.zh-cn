---
title: CD2DLinearGradientBrush 类
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: d87cdae5c24eae391be8db2fcdd04f91d592e427
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753156"
---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush 类

ID2D1线性渐变笔的包装器。

## <a name="syntax"></a>语法

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D线性梯度画笔：CD2D线性梯度画笔](#cd2dlineargradientbrush)|构造 CD2D 线性渐变画笔对象。|
|[CD2D线性梯度画笔：*CD2D线性梯度画笔](#_dtorcd2dlineargradientbrush)|析构函数。 销毁 D2D 线性渐变画笔对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D线性渐变画笔：：附加](#attach)|将现有资源接口附加到对象|
|[CD2D线性渐变画笔：：创建](#create)|创建 CD2D 线性渐变画笔。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2D线性梯度画笔：:D](#destroy)|销毁 CD2D 线性渐变画笔对象。 （覆盖[CD2D 梯度画笔：:Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).）|
|[CD2D线性梯度画笔：:D](#detach)|从对象分离资源接口|
|[CD2D线性渐变画笔：获取](#get)|返回 ID2D1 线性渐变画笔接口|
|[CD2D线性梯度画笔：：获取端点](#getendpoint)|检索线性渐变的结束坐标|
|[CD2D线性梯度画笔：：获取起始点](#getstartpoint)|检索线性渐变的起始坐标|
|[CD2D线性渐变画笔：：设置结束点](#setendpoint)|设置画笔坐标空间中线性渐变的结束坐标|
|[CD2D线性渐变画笔：：设置起始点](#setstartpoint)|设置画笔坐标空间中线性渐变的起始坐标|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2D线性渐变笔刷：：操作员 ID2D1 线性渐变笔刷*](#operator_id2d1lineargradientbrush_star)|返回 ID2D1 线性渐变画笔接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D线性渐变画笔：：m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|渐变的开始和结束点。|
|[CD2D线性渐变画笔：：m_pLinearGradientBrush](#m_plineargradientbrush)|指向 ID2D1 线性渐变画笔的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2D 梯度画笔](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2D线性梯度画笔：*CD2D线性梯度画笔

析构函数。 销毁 D2D 线性渐变画笔对象时调用。

```
virtual ~CD2DLinearGradientBrush();
```

## <a name="cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2D线性渐变画笔：：附加

将现有资源接口附加到对象

```cpp
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2D线性梯度画笔：CD2D线性梯度画笔

构造 CD2D 线性渐变画笔对象。

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

*p 父目标*<br/>
指向渲染目标的指针。

*梯度停止*<br/>
指向D2D1_GRADIENT_STOP结构数组的指针。

*梯度停止计数*<br/>
大于或等于 1 的值，用于指定渐变停止数组中的渐变停止数。

*线性渐变画笔属性*<br/>
渐变的开始和结束点。

*颜色插值伽马*<br/>
在渐变停止之间执行颜色插值的空间。

*扩展模式*<br/>
渐变在 [0，1] 规范化范围之外的行为。

*pBrush 属性*<br/>
指向画笔的不一用性和变换的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2D线性渐变画笔：：创建

创建 CD2D 线性渐变画笔。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2D线性梯度画笔：:D

销毁 CD2D 线性渐变画笔对象。

```
virtual void Destroy();
```

## <a name="cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2D线性梯度画笔：:D

从对象分离资源接口

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dlineargradientbrushget"></a><a name="get"></a>CD2D线性渐变画笔：获取

返回 ID2D1 线性渐变画笔接口

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1线性渐变笔刷接口或 NULL 的指针。

## <a name="cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2D线性梯度画笔：：获取端点

检索线性渐变的结束坐标

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>返回值

画笔坐标空间中线性渐变的结束二维坐标

## <a name="cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2D线性梯度画笔：：获取起始点

检索线性渐变的起始坐标

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>返回值

画笔坐标空间中线性渐变的起始二维坐标

## <a name="cd2dlineargradientbrushm_lineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2D线性渐变画笔：：m_LinearGradientBrushProperties

渐变的开始和结束点。

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

## <a name="cd2dlineargradientbrushm_plineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2D线性渐变画笔：：m_pLinearGradientBrush

指向 ID2D1 线性渐变画笔的指针。

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

## <a name="cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2D线性渐变笔刷：：操作员 ID2D1 线性渐变笔刷*

返回 ID2D1 线性渐变画笔接口

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1线性渐变笔刷接口或 NULL 的指针。

## <a name="cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2D线性渐变画笔：：设置结束点

设置画笔坐标空间中线性渐变的结束坐标

```cpp
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>参数

*点*<br/>
画笔坐标空间中线性渐变的结束二维坐标

## <a name="cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2D线性渐变画笔：：设置起始点

设置画笔坐标空间中线性渐变的起始坐标

```cpp
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>参数

*点*<br/>
画笔坐标空间中线性渐变的起始二维坐标

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
