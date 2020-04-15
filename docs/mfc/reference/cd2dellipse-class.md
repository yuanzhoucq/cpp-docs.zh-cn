---
title: CD2DEllipse 类
ms.date: 08/29/2019
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 82ad2fbfb8558486134f85d7ec9bcaa6eb4e7507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369258"
---
# <a name="cd2dellipse-class"></a>CD2DEllipse 类

`D2D1_ELLIPSE`的包装器。

## <a name="syntax"></a>语法

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DEllipse：CD2DEllipse](#cd2dellipse)|已重载。 从`CD2DEllipse``D2D1_ELLIPSE`对象构造对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dellipsecd2dellipse"></a><a name="cd2dellipse"></a>CD2DEllipse：CD2DEllipse

从 CD2DRectF 对象构造 CD2DEllipse 对象。

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>参数

*矩形*<br/>
源矩形

*ellipse*<br/>
源椭圆

*ptCenter*<br/>
椭圆的中心点。

*大小半径*<br/>
椭圆的 X 半径和 Y 半径。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
