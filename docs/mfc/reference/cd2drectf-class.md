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
ms.openlocfilehash: 9b91cfaec3827a61152c4116b56e817a436606be
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682403"
---
# <a name="cd2drectf-class"></a>CD2DRectF 类

`D2D1_RECT_F`的包装器。

## <a name="syntax"></a>语法

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|已重载。 `CD2DRectF` 从`D2D1_RECT_F`对象构造对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|返回一个**布尔**值, 该值指示表达式是否不包含有效数据 (NULL)。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DRectF:: operator CRect](#operator_crect)|转换`CD2DRectF` 为`CRect`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>要求

**标头:** afxrendertarget

##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF

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

*rect*<br/>
源矩形

*fLeft*<br/>
源左坐标

*fTop*<br/>
源顶层坐标

*fRight*<br/>
源右坐标

*fBottom*<br/>
源下坐标

##  <a name="isnull"></a>  CD2DRectF::IsNull

返回一个布尔值, 该值指示表达式是否不包含有效数据 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果矩形的上、左、下、右值全部等于 0, 则为 TRUE;否则为 FALSE。

##  <a name="operator_crect"></a>  CD2DRectF::operator CRect

将 CD2DRectF 转换为 CRect 对象。

```
operator CRect();
```

### <a name="return-value"></a>返回值

D2D 矩形的当前值。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
