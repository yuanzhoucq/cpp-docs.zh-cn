---
title: CD2DSolidColorBrush 类
ms.date: 03/27/2019
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
ms.openlocfilehash: 5aa3d7688046b0c1b04983f2d27fe5579dd7c680
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369058"
---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush 类

ID2D1SolidColorBrush 的包装器。

## <a name="syntax"></a>语法

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D纯色笔：：CD2D纯色笔](#cd2dsolidcolorbrush)|已重载。 构造 CD2DSolidColorBrush 对象。|
|[CD2D纯色笔：：*CD2D纯色刷](#_dtorcd2dsolidcolorbrush)|析构函数。 销毁 D2D 实体画笔对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D 纯色笔：：附加](#attach)|将现有资源接口附加到对象|
|[CD2D纯色笔：：创建](#create)|创建 CD2D 纯色画笔。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2D纯色笔：:D](#destroy)|销毁 CD2DSolidColorBrush 对象。 （覆盖[CD2DBrush：:Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).）|
|[CD2D纯色笔：:D](#detach)|从对象分离资源接口|
|[CD2D纯色笔：获取](#get)|返回 ID2D1 纯色笔接口|
|[CD2D纯色笔：：获取颜色](#getcolor)|检索纯色画笔的颜色|
|[CD2D纯色笔：：设置颜色](#setcolor)|指定此纯色画笔的颜色|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2D纯色笔：：操作员 ID2D1 纯色笔*](#operator_id2d1solidcolorbrush_star)|返回 ID2D1 纯色笔接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D纯色笔：：m_colorSolid](#m_colorsolid)|刷纯色。|
|[CD2D纯色笔：：m_pSolidColorBrush](#m_psolidcolorbrush)|存储指向 ID2D1SolidColorBrush 对象的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2D纯色笔刷](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a>CD2D纯色笔：：*CD2D纯色刷

析构函数。 销毁 D2D 实体画笔对象时调用。

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a>CD2D 纯色笔：：附加

将现有资源接口附加到对象

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a>CD2D纯色笔：：CD2D纯色笔

构造 CD2DSolidColorBrush 对象。

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*颜色*<br/>
画笔颜色的红色、绿色、蓝色和 alpha 值。

*pBrush 属性*<br/>
指向画笔的不一用性和变换的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

*n阿尔法*<br/>
画笔颜色的不恰当性。

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a>CD2D纯色笔：：创建

创建 CD2D 纯色画笔。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a>CD2D纯色笔：:D

销毁 CD2DSolidColorBrush 对象。

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a>CD2D纯色笔：:D

从对象分离资源接口

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a>CD2D纯色笔：获取

返回 ID2D1 纯色笔接口

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1SolidColorBrush 接口或 NULL 的指针。

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a>CD2D纯色笔：：获取颜色

检索纯色画笔的颜色

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>返回值

此纯色画笔的颜色

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a>CD2D纯色笔：：m_colorSolid

刷纯色。

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a>CD2D纯色笔：：m_pSolidColorBrush

存储指向 ID2D1SolidColorBrush 对象的指针。

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a>CD2D纯色笔：：操作员 ID2D1 纯色笔*

返回 ID2D1 纯色笔接口

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1SolidColorBrush 接口或 NULL 的指针。

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a>CD2D纯色笔：：设置颜色

指定此纯色画笔的颜色

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
此纯色画笔的颜色

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
