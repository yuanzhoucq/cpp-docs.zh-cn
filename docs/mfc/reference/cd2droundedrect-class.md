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
ms.openlocfilehash: 5189f3d824c008845570eac6eead4a35be1e483d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369076"
---
# <a name="cd2droundedrect-class"></a>CD2DRoundedRect 类

`D2D1_ROUNDED_RECT`的包装器。

## <a name="syntax"></a>语法

```
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D 四舍五入：CD2D 四舍五入](#cd2droundedrect)|已重载。 从`CD2DRoundedRect``D2D1_ROUNDED_RECT`对象构造对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_ROUNDED_RECT`

[CD2D 四舍五入](../../mfc/reference/cd2droundedrect-class.md)

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2droundedrectcd2droundedrect"></a><a name="cd2droundedrect"></a>CD2D 四舍五入：CD2D 四舍五入

从 CD2DRectF 对象构造 CD2D 四舍五入重新对象。

```
CD2DRoundedRect(
    const CD2DRectF& rectIn,
    const CD2DSizeF& sizeRadius);

CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```

### <a name="parameters"></a>参数

*雷金*<br/>
源矩形

*大小半径*<br/>
半径大小

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
