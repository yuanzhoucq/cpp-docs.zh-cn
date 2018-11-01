---
title: CD2DRoundedRect 类
ms.date: 11/04/2016
f1_keywords:
- CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect::CD2DRoundedRect
helpviewer_keywords:
- CD2DRoundedRect [MFC], CD2DRoundedRect
ms.assetid: 06207fb5-e92b-41c0-bceb-b45d8f466531
ms.openlocfilehash: 6c1aa2bb9593cdf12aadc39ef8a85cc8ad14078a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677469"
---
# <a name="cd2droundedrect-class"></a>CD2DRoundedRect 类

`D2D1_ROUNDED_RECT`的包装器。

## <a name="syntax"></a>语法

```
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DRoundedRect::CD2DRoundedRect](#cd2droundedrect)|已重载。 构造`CD2DRoundedRect`对象从`D2D1_ROUNDED_RECT`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_ROUNDED_RECT`

[CD2DRoundedRect](../../mfc/reference/cd2droundedrect-class.md)

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="cd2droundedrect"></a>  CD2DRoundedRect::CD2DRoundedRect

构造 CD2DRectF 对象从一个 CD2DRoundedRect 对象。

```
CD2DRoundedRect(
    const CD2DRectF& rectIn,
    const CD2DSizeF& sizeRadius);

CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```

### <a name="parameters"></a>参数

*rectIn*<br/>
源矩形

*sizeRadius*<br/>
半径大小

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
