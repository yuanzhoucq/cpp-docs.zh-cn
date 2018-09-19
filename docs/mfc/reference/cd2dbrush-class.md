---
title: CD2DBrush 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7141350d318673b5458cd760f7ad9d48a466bda
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409774"
---
# <a name="cd2dbrush-class"></a>CD2DBrush 类

ID2D1Brush 包装器。

## <a name="syntax"></a>语法

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|构造一个 CD2DBrush 对象。|
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
|[CD2DBrush::IsValid](#isvalid)|检查资源有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2DBrush::SetOpacity](#setopacity)|设置此画笔的不透明度|
|[CD2DBrush::SetTransform](#settransform)|指定的转换应用于呈现器目标，替换现有转换。 所有后续的绘图操作将在转换后的空间|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DBrush::operator ID2D1Brush *](#operator_id2d1brush_star)|返回 ID2D1Brush 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|存储指向 ID2D1Brush 对象的指针。|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|画笔属性。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="_dtorcd2dbrush"></a>  CD2DBrush:: ~ CD2DBrush

析构函数。 当 D2D 画笔对象被销毁时调用。

```
virtual ~CD2DBrush();
```

##  <a name="attach"></a>  CD2DBrush::Attach

附加现有的资源的对象的接口。

```
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>参数

*pResource*<br/>
现有资源的接口。 不能为 NULL。

##  <a name="cd2dbrush"></a>  CD2DBrush::CD2DBrush

构造一个 CD2DBrush 对象。

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*pParentTarget*<br/>
指向该呈现器目标的指针。

*pBrushProperties*<br/>
一个指向不透明度和画笔的转换。

*bAutoDestroy*<br/>
指示所有者 (pParentTarget) 将销毁该对象。

##  <a name="destroy"></a>  CD2DBrush::Destroy

销毁 CD2DBrush 对象。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBrush::Detach

分离对象中的资源接口。

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>返回值

指向已分离的资源接口指针。

##  <a name="get"></a>  CD2DBrush::Get

返回 ID2D1Brush 接口

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>返回值

指向 ID2D1Brush 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="getopacity"></a>  CD2DBrush::GetOpacity

获取此画笔的不透明度

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>返回值

一个介于 0 和 1，指示不透明度的画笔之间的值。 此值是以线性方式缩放画笔填充的所有像素的 alpha 值的常量乘数。 不透明度值是 0 到 1 范围限制为之前它们将全部相乘。

##  <a name="gettransform"></a>  CD2DBrush::GetTransform

获取当前呈现器目标的转换

```
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>参数

*transform*<br/>
当此方法返回时，包含当前呈现器目标的转换。 此参数未经初始化即被传递。

##  <a name="isvalid"></a>  CD2DBrush::IsValid

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源是有效，则为，TRUE否则为 FALSE。

##  <a name="m_pbrush"></a>  CD2DBrush::m_pBrush

存储指向 ID2D1Brush 对象的指针。

```
ID2D1Brush* m_pBrush;
```

##  <a name="m_pbrushproperties"></a>  CD2DBrush::m_pBrushProperties

画笔属性。

```
CD2DBrushProperties* m_pBrushProperties;
```

##  <a name="operator_id2d1brush_star"></a>  CD2DBrush::operator ID2D1Brush *

返回 ID2D1Brush 接口

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>返回值

指向 ID2D1Brush 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="setopacity"></a>  CD2DBrush::SetOpacity

设置此画笔的不透明度

```
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>参数

*不透明度*<br/>
一个介于 0 和 1，指示不透明度的画笔之间的值。 此值是以线性方式缩放画笔填充的所有像素的 alpha 值的常量乘数。 不透明度值是 0 到 1 范围限制为之前它们将全部相乘。

##  <a name="settransform"></a>  CD2DBrush::SetTransform

指定的转换应用于呈现器目标，替换现有转换。 所有后续的绘图操作将在转换后的空间。

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>参数

*transform*<br/>
要应用到呈现目标的转换

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
