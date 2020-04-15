---
title: CD2DBitmapBrush 类
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: e26202392bf4783598aec0dddfea514fce806a8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369300"
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush 类

ID2D1 位地图画笔的包装器。

## <a name="syntax"></a>语法

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DBitmapBrush：：CD2DBitmapBrush](#cd2dbitmapbrush)|已重载。 从文件构造 CD2DBitmapBrush 对象。|
|[CD2DBitmapBrush：*CD2DBitmapBrush](#dtor)|析构函数。 销毁 D2D 位图画笔对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DBitmapBrush：：附加](#attach)|将现有资源接口附加到对象|
|[CD2DBitmapBrush：创建](#create)|创建 CD2DBitmapBrush。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2DBitmapBrush：:D](#destroy)|销毁 CD2DBitmapBrush 对象。 （覆盖[CD2DBrush：:Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).）|
|[CD2DBitmapBrush：:Detach](#detach)|从对象分离资源接口|
|[CD2DBitmapBrush：获取](#get)|返回 ID2D1 位地图画笔接口|
|[CD2DBitmapBrush：：获取位图](#getbitmap)|获取此画笔用于绘制的位图源|
|[CD2DBitmapBrush：：获取扩展模式X](#getextendmodex)|获取画笔水平放置超出其位图的区域的方法|
|[CD2DBitmapBrush：获取扩展模式](#getextendmodey)|获取画笔垂直绘制超出其位图的区域切片的方法|
|[CD2DBitmapBrush：获取插值模式](#getinterpolationmode)|获取缩放或旋转画笔位图时使用的插值方法|
|[CD2DBitmapBrush：：设置位图](#setbitmap)|指定此画笔用于绘制的位图源|
|[CD2DBitmapBrush：：设置扩展模式X](#setextendmodex)|指定画笔如何水平放置那些延伸到其位图的区域|
|[CD2DBitmapBrush：：设置扩展模式](#setextendmodey)|指定画笔如何垂直绘制超出其位图的区域的切片|
|[CD2DBitmapBrush：设置插值模式](#setinterpolationmode)|指定缩放或旋转画笔位贴图时使用的插值模式|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CD2DBitmapBrush：：通用](#commoninit)|初始化对象|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DBitmapBrush：：操作员 ID2D1 位地图画笔*](#operator_id2d1bitmapbrush_star)|返回 ID2D1 位地图画笔接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2DBitmapBrush：m_pBitmap](#m_pbitmap)|存储指向 CD2DBitmap 对象的指针。|
|[CD2DBitmapBrush：：m_pBitmapBrush](#m_pbitmapbrush)|存储指向 ID2D1BitmapBrush 对象的指针。|
|[CD2DBitmapBrush：：m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|位图画笔属性。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a>CD2DBitmapBrush：*CD2DBitmapBrush

析构函数。 销毁 D2D 位图画笔对象时调用。

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a>CD2DBitmapBrush：：附加

将现有资源接口附加到对象

```
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a>CD2DBitmapBrush：：CD2DBitmapBrush

构造 CD2DBitmapBrush 对象。

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*pBitmapBrush 属性*<br/>
指向扩展模式的指针和位图画笔的插值模式。

*pBrush 属性*<br/>
指向画笔的不一用性和变换的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

*uiResID*<br/>
资源的资源 ID 号。

*lpszType*<br/>
指向包含资源类型的空端字符串的指针。

*大小 D 最大*<br/>
位图的目标大小。

*lpsz图像路径*<br/>
指向包含文件名称的 null 终止字符串的指针。

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a>CD2DBitmapBrush：：通用

初始化对象

```
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>参数

*pBitmapBrush 属性*<br/>
指向位图画笔属性的指针。

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a>CD2DBitmapBrush：创建

创建 CD2DBitmapBrush。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a>CD2DBitmapBrush：:D

销毁 CD2DBitmapBrush 对象。

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a>CD2DBitmapBrush：:Detach

从对象分离资源接口

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dbitmapbrushget"></a><a name="get"></a>CD2DBitmapBrush：获取

返回 ID2D1 位地图画笔接口

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1BitmapBrush 接口或 NULL 的指针。

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a>CD2DBitmapBrush：：获取位图

获取此画笔用于绘制的位图源

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 CD2DBitmap 对象或 NULL 的指针。

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a>CD2DBitmapBrush：：获取扩展模式X

获取画笔水平放置超出其位图的区域的方法

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>返回值

指定画笔如何水平放置那些延伸到其位图的区域的值

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a>CD2DBitmapBrush：获取扩展模式

获取画笔垂直绘制超出其位图的区域切片的方法

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>返回值

指定画笔如何垂直绘制超出其位图的区域的切片的值

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a>CD2DBitmapBrush：获取插值模式

获取缩放或旋转画笔位图时使用的插值方法

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>返回值

缩放或旋转画笔位图时使用的插值方法

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmapBrush：m_pBitmap

存储指向 CD2DBitmap 对象的指针。

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a>CD2DBitmapBrush：：m_pBitmapBrush

存储指向 ID2D1BitmapBrush 对象的指针。

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush：：m_pBitmapBrushProperties

位图画笔属性。

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush：：操作员 ID2D1 位地图画笔*

返回 ID2D1 位地图画笔接口

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1BitmapBrush 接口或 NULL 的指针。

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a>CD2DBitmapBrush：：设置位图

指定此画笔用于绘制的位图源

```
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>参数

*pBitmap*<br/>
画笔使用的位图源

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a>CD2DBitmapBrush：：设置扩展模式X

指定画笔如何水平放置那些延伸到其位图的区域

```
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>参数

*扩展模式X*<br/>
指定画笔如何水平放置那些延伸到其位图的区域的值

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a>CD2DBitmapBrush：：设置扩展模式

指定画笔如何垂直绘制超出其位图的区域的切片

```
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>参数

*扩展模式*<br/>
指定画笔如何垂直绘制超出其位图的区域的切片的值

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a>CD2DBitmapBrush：设置插值模式

指定缩放或旋转画笔位贴图时使用的插值模式

```
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>参数

*插值模式*<br/>
缩放或旋转画笔位图时使用的插值模式

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
