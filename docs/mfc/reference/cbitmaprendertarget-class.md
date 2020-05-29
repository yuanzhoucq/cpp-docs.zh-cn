---
title: CBitmapRenderTarget 类
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: 8ba8c8819b47185315d67d732fc90ab2ffc0ad0a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752931"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget 类

ID2D1BitmapRenderTarget 的包装。

## <a name="syntax"></a>语法

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 位映射渲染目标：：C 位贴图渲染目标](#cbitmaprendertarget)|构造 CBitmapRenderTarget 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CBitmap渲染目标：：附加](#attach)|将现有渲染目标接口附加到对象|
|[CBitmapRender目标：:D](#detach)|从对象分离渲染目标接口|
|[C 位映射渲染目标：：获取位图](#getbitmap)|检索此渲染目标的位图。 返回的位图可用于绘图操作。|
|[C 位贴图渲染目标：：获取位贴图渲染目标](#getbitmaprendertarget)|返回 ID2D1 位映射渲染目标接口|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CBitmap渲染目标：：运算符 ID2D1 位贴图渲染目标*](#operator_id2d1bitmaprendertarget_star)|返回 ID2D1 位映射渲染目标接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CBitmap渲染目标：：m_pBitmapRenderTarget](#m_pbitmaprendertarget)|指向 ID2D1BitmapRenderTarget 对象的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CRender目标](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cbitmaprendertargetattach"></a><a name="attach"></a>CBitmap渲染目标：：附加

将现有渲染目标接口附加到对象

```cpp
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>参数

*p目标*<br/>
现有渲染目标接口。 不能为 NULL

## <a name="cbitmaprendertargetcbitmaprendertarget"></a><a name="cbitmaprendertarget"></a>C 位映射渲染目标：：C 位贴图渲染目标

构造 CBitmapRenderTarget 对象。

```
CBitmapRenderTarget();
```

## <a name="cbitmaprendertargetdetach"></a><a name="detach"></a>CBitmapRender目标：:D

从对象分离渲染目标接口

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>返回值

指向分离的渲染目标接口的指针。

## <a name="cbitmaprendertargetgetbitmap"></a><a name="getbitmap"></a>C 位映射渲染目标：：获取位图

检索此渲染目标的位图。 返回的位图可用于绘图操作。

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>参数

*位图*<br/>
当此方法返回时，包含此渲染目标的有效位图。 此位图可用于绘图操作。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cbitmaprendertargetgetbitmaprendertarget"></a><a name="getbitmaprendertarget"></a>C 位贴图渲染目标：：获取位贴图渲染目标

返回 ID2D1 位映射渲染目标接口

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1BitmapRenderTarget 接口或 NULL 的指针。

## <a name="cbitmaprendertargetm_pbitmaprendertarget"></a><a name="m_pbitmaprendertarget"></a>CBitmap渲染目标：：m_pBitmapRenderTarget

指向 ID2D1BitmapRenderTarget 对象的指针。

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

## <a name="cbitmaprendertargetoperator-id2d1bitmaprendertarget"></a><a name="operator_id2d1bitmaprendertarget_star"></a>CBitmap渲染目标：：运算符 ID2D1 位贴图渲染目标*

返回 ID2D1 位映射渲染目标接口

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1BitmapRenderTarget 接口或 NULL 的指针。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
