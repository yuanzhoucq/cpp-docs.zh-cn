---
title: CD2DRectU 类
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: 26e647ae01a498a6ad8ca2d7c866f33b01910881
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369110"
---
# <a name="cd2drectu-class"></a>CD2DRectU 类

`D2D1_RECT_U`的包装器。

## <a name="syntax"></a>语法

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DRectU：：CD2DRectU](#cd2drectu)|已重载。 从`CD2DRectU``D2D1_RECT_U`对象构造对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DRectU：：IsNull](#isnull)|返回**一个布尔值**，指示表达式是否不包含有效数据 （NULL）。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DRectU：：操作员CRect](#operator_crect)|转换为`CD2DRectU``CRect`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a>CD2DRectU：：CD2DRectU

从 CRect 对象构造 CD2DRectU 对象。

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>参数

*矩形*<br/>
源矩形

*u 左*<br/>
源左坐标

*uTop*<br/>
源顶部坐标

*uRight*<br/>
源右坐标

*u巴斯特*<br/>
源底部坐标

## <a name="cd2drectuisnull"></a><a name="isnull"></a>CD2DRectU：：IsNull

返回一个布尔值，指示表达式是否不包含有效数据 （Null）。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果矩形的顶部、左侧、底部和右侧值都等于 0，则为 TRUE;否则 FALSE。

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a>CD2DRectU：：操作员CRect

将 CD2DRectU 转换为 CRect 对象。

```
operator CRect();
```

### <a name="return-value"></a>返回值

D2D 矩形的当前值。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
