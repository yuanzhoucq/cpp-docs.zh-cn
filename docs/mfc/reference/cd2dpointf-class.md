---
title: CD2DPointF 类
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: b8fe808c3147fa52c5041e2988822ace0ba60896
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304036"
---
# <a name="cd2dpointf-class"></a>CD2DPointF 类

`D2D1_POINT_2F`的包装器。

## <a name="syntax"></a>语法

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DPointF::CD2DPointF](#cd2dpointf)|已重载。 构造`CD2DPointF`对象从`D2D1_POINT_2F`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DPointF::operator CPoint](#operator_cpoint)|将转换`CD2DPointF`到`CPoint`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF

构造 CPoint 对象从一个 CD2DPointF 对象。

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>参数

*pt*<br/>
源点

*fX*<br/>
源 X

*fY*<br/>
source Y

##  <a name="operator_cpoint"></a>  CD2DPointF::operator CPoint

将 CD2DPointF 转换为 CPoint 对象。

```
operator CPoint();
```

### <a name="return-value"></a>返回值

D2D 点的当前值。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
