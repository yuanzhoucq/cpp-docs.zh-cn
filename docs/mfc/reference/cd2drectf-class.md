---
title: CD2DRectF 类
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 33d3c5f9e795ad6c91b689436e8a3b1b56966dce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369122"
---
# <a name="cd2drectf-class"></a>CD2DRectF 类

`D2D1_RECT_F`的包装器。

## <a name="syntax"></a>语法

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DrectF：CD2DrectF](#cd2drectf)|已重载。 从`CD2DRectF``D2D1_RECT_F`对象构造对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DrectF：：IsNull](#isnull)|返回**一个布尔值**，指示表达式是否不包含有效数据 （NULL）。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DRectF：：运算符 CRect](#operator_crect)|转换为`CD2DRectF``CRect`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a>CD2DrectF：CD2DrectF

从 CRect 对象构造 CD2DRectF 对象。

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>参数

*矩形*<br/>
源矩形

*f左*<br/>
源左坐标

*fTop*<br/>
源顶部坐标

*恐惧*<br/>
源右坐标

*fBottom*<br/>
源底部坐标

## <a name="cd2drectfisnull"></a><a name="isnull"></a>CD2DrectF：：IsNull

返回一个布尔值，指示表达式是否不包含有效数据 （Null）。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果矩形的顶部、左侧、底部和右侧值都等于 0，则为 TRUE;否则 FALSE。

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a>CD2DRectF：：运算符 CRect

将 CD2DRectF 转换为 CRect 对象。

```
operator CRect();
```

### <a name="return-value"></a>返回值

D2D 矩形的当前值。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
