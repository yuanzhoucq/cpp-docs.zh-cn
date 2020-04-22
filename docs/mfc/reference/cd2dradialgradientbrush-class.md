---
title: CD2DRadialGradientBrush 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: 450314fdbf8441b0cc345430518d083573659add
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750316"
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush 类

用于 ID2D1 Radial 梯度画笔的包装器。

## <a name="syntax"></a>语法

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D 径梯度刷：：CD2D 半径梯度刷](#cd2dradialgradientbrush)|构造 CD2D 线性渐变画笔对象。|
|[CD2D 径梯度刷：*CD2D半径梯度刷](#_dtorcd2dradialgradientbrush)|析构函数。 销毁 D2D 径向渐变画笔对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D 辐射梯度画笔：：附加](#attach)|将现有资源接口附加到对象|
|[CD2D 半径渐变画笔：：创建](#create)|创建 CD2DRadial 渐变画笔。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2DRadial梯度刷：:D](#destroy)|销毁 CD2DRadial 梯度画笔对象。 （覆盖[CD2D 梯度画笔：:Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).）|
|[CD2DRadial 梯度画笔：:D](#detach)|从对象分离资源接口|
|[CD2D 半径梯度画笔：获取](#get)|返回 ID2D1 径向渐变画笔接口|
|[CD2D 半径梯度画笔：：获取中心](#getcenter)|检索渐变椭圆的中心|
|[CD2D 半径梯度画笔：：获取梯度原点偏移](#getgradientoriginoffset)|检索渐变原点的偏移量相对于渐变椭圆的中心|
|[CD2D 半径梯度画笔：：获取 RadiusX](#getradiusx)|检索渐变椭圆的 x 半径|
|[CD2D 半径梯度画笔：：获取半径](#getradiusy)|检索渐变椭圆的 y 半径|
|[CD2D 半径梯度画笔：：设置中心](#setcenter)|指定画笔坐标空间中渐变椭圆的中心|
|[CD2D 半径梯度画笔：：设置渐变原点偏移](#setgradientoriginoffset)|指定渐变原点的偏移量相对于渐变椭圆的中心|
|[CD2D 半径梯度画笔：：SetRadiusX](#setradiusx)|在画笔的坐标空间中指定渐变椭圆的 x 半径|
|[CD2D 半径梯度画笔：：SetRadiusY](#setradiusy)|在画笔的坐标空间中指定渐变椭圆的 y 半径|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2D 辐射梯度画笔：：操作员 ID2D1 辐射梯度画笔*](#operator_id2d1radialgradientbrush_star)|返回 ID2D1 径向渐变画笔接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D 辐射梯度画笔：：m_pRadialGradientBrush](#m_pradialgradientbrush)|指向 ID2D1 Radial 梯度画笔的指针。|
|[CD2D半径梯度画笔：：m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|画笔渐变的中心、渐变原点偏移以及 x 半径和 y 半径。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2D 梯度画笔](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a>CD2D 径梯度刷：*CD2D半径梯度刷

析构函数。 销毁 D2D 径向渐变画笔对象时调用。

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a>CD2D 辐射梯度画笔：：附加

将现有资源接口附加到对象

```cpp
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a>CD2D 径梯度刷：：CD2D 半径梯度刷

构造 CD2D 线性渐变画笔对象。

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

*p 父目标*<br/>
指向渲染目标的指针。

*梯度停止*<br/>
指向D2D1_GRADIENT_STOP结构数组的指针。

*梯度停止计数*<br/>
大于或等于 1 的值，用于指定渐变停止数组中的渐变停止数。

*径向渐变画笔属性*<br/>
画笔渐变的中心、渐变原点偏移以及 x 半径和 y 半径。

*颜色插值伽马*<br/>
在渐变停止之间执行颜色插值的空间。

*扩展模式*<br/>
渐变在 [0，1] 规范化范围之外的行为。

*pBrush 属性*<br/>
指向画笔的不一用性和变换的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a>CD2D 半径渐变画笔：：创建

创建 CD2DRadial 渐变画笔。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a>CD2DRadial梯度刷：:D

销毁 CD2DRadial 梯度画笔对象。

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a>CD2DRadial 梯度画笔：:D

从对象分离资源接口

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a>CD2D 半径梯度画笔：获取

返回 ID2D1 径向渐变画笔接口

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Radial 梯度画笔接口或 NULL 的指针。

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a>CD2D 半径梯度画笔：：获取中心

检索渐变椭圆的中心

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>返回值

渐变椭圆的中心。 此值在画笔的坐标空间中表示

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a>CD2D 半径梯度画笔：：获取梯度原点偏移

检索渐变原点的偏移量相对于渐变椭圆的中心

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>返回值

渐变原点的偏移量来自渐变椭圆的中心。 此值在画笔的坐标空间中表示

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a>CD2D 半径梯度画笔：：获取 RadiusX

检索渐变椭圆的 x 半径

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>返回值

渐变椭圆的 x 半径。 此值在画笔的坐标空间中表示

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a>CD2D 半径梯度画笔：：获取半径

检索渐变椭圆的 y 半径

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>返回值

渐变椭圆的 y 半径。 此值在画笔的坐标空间中表示

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a>CD2D 辐射梯度画笔：：m_pRadialGradientBrush

指向 ID2D1 Radial 梯度画笔的指针。

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a>CD2D半径梯度画笔：：m_RadialGradientBrushProperties

画笔渐变的中心、渐变原点偏移以及 x 半径和 y 半径。

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a>CD2D 辐射梯度画笔：：操作员 ID2D1 辐射梯度画笔*

返回 ID2D1 径向渐变画笔接口

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Radial 梯度画笔接口或 NULL 的指针。

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a>CD2D 半径梯度画笔：：设置中心

指定画笔坐标空间中渐变椭圆的中心

```cpp
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>参数

*点*<br/>
渐变椭圆的中心，位于画笔的坐标空间中

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a>CD2D 半径梯度画笔：：设置渐变原点偏移

指定渐变原点的偏移量相对于渐变椭圆的中心

```cpp
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>参数

*梯度原点偏移*<br/>
渐变原点的偏移量来自渐变椭圆的中心

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a>CD2D 半径梯度画笔：：SetRadiusX

在画笔的坐标空间中指定渐变椭圆的 x 半径

```cpp
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>参数

*半径X*<br/>
渐变椭圆的 x 半径。 此值位于画笔的坐标空间中

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a>CD2D 半径梯度画笔：：SetRadiusY

在画笔的坐标空间中指定渐变椭圆的 y 半径

```cpp
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>参数

*半径Y*<br/>
渐变椭圆的 y 半径。 此值位于画笔的坐标空间中

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
