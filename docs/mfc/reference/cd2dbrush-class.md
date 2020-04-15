---
title: CD2DBrush 类
ms.date: 11/04/2016
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
ms.openlocfilehash: d03fb6f398e18957f68fc18c78d8a397efc67506
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369278"
---
# <a name="cd2dbrush-class"></a>CD2DBrush 类

ID2D1Brush 的包装器。

## <a name="syntax"></a>语法

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CD2DBrush：CD2DBrush](#cd2dbrush)|构造 CD2DBrush 对象。|
|[CD2DBrush：*CD2DBrush](#_dtorcd2dbrush)|析构函数。 销毁 D2D 画笔对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DBrush：附加](#attach)|将现有资源接口附加到对象|
|[CD2DBrush：:D](#destroy)|销毁 CD2DBrush 对象。 （覆盖[CD2D 资源：:D）](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2DBrush：:D](#detach)|从对象分离资源接口|
|[CD2DBrush：获取](#get)|返回 ID2D1Brush 接口|
|[CD2DBrush：获取机会](#getopacity)|获取此画笔的不恰当程度|
|[CD2DBrush：获取转换](#gettransform)|获取渲染目标的当前变换|
|[CD2DBrush：有效](#isvalid)|检查资源有效性（覆盖[CD2D 资源：：有效](../../mfc/reference/cd2dresource-class.md#isvalid)。）|
|[CD2DBrush：SetOpaa](#setopacity)|设置此画笔的不恰当程度|
|[CD2DBrush：：设置转换](#settransform)|将指定的转换应用于渲染目标，替换现有变换。 所有后续绘图操作都发生在转换的空间中|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DBrush：：操作员 ID2D1Brush*](#operator_id2d1brush_star)|返回 ID2D1Brush 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2DBrush：m_pBrush](#m_pbrush)|存储指向 ID2D1Brush 对象的指针。|
|[CD2DBrush：m_pBrushProperties](#m_pbrushproperties)|画笔属性。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a>CD2DBrush：*CD2DBrush

析构函数。 销毁 D2D 画笔对象时调用。

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a>CD2DBrush：附加

将现有资源接口附加到对象。

```
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL。

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a>CD2DBrush：CD2DBrush

构造 CD2DBrush 对象。

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*pBrush 属性*<br/>
指向画笔的不一用性和变换的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a>CD2DBrush：:D

销毁 CD2DBrush 对象。

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a>CD2DBrush：:D

从对象分离资源接口。

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dbrushget"></a><a name="get"></a>CD2DBrush：获取

返回 ID2D1Brush 接口

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Brush 接口或 NULL 的指针。

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a>CD2DBrush：获取机会

获取此画笔的不恰当程度

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>返回值

零和 1 之间的值，指示画笔的不恰当性。 此值是一个常量乘数，它线性缩放画笔填充的所有像素的 alpha 值。 不一元值在乘以 0 到 1 的范围内夹紧， 然后再相乘。

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a>CD2DBrush：获取转换

获取渲染目标的当前变换

```
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>参数

*transform*<br/>
当返回时，包含渲染目标的当前变换。 此参数在传递时尚未初始化。

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a>CD2DBrush：有效

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则 FALSE。

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a>CD2DBrush：m_pBrush

存储指向 ID2D1Brush 对象的指针。

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a>CD2DBrush：m_pBrushProperties

画笔属性。

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a>CD2DBrush：：操作员 ID2D1Brush*

返回 ID2D1Brush 接口

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Brush 接口或 NULL 的指针。

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a>CD2DBrush：SetOpaa

设置此画笔的不恰当程度

```
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>参数

*透明度*<br/>
零和 1 之间的值，指示画笔的不恰当性。 此值是一个常量乘数，它线性缩放画笔填充的所有像素的 alpha 值。 不一元值在乘以 0 到 1 的范围内夹紧， 然后再相乘。

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a>CD2DBrush：：设置转换

将指定的转换应用于渲染目标，替换现有变换。 所有后续绘图操作都发生在转换的空间中。

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>参数

*transform*<br/>
应用于渲染目标的转换

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
