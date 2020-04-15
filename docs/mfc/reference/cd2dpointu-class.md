---
title: CD2DPointU 类
ms.date: 08/29/2019
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 8c6db55f1dde1fd054a1f75590f5969c097b2f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369145"
---
# <a name="cd2dpointu-class"></a>CD2DPointU 类

`D2D1_POINT_2U`的包装器。

## <a name="syntax"></a>语法

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DPointU：CD2DPointU](#cd2dpointu)|已重载。 从对象`D2D1_POINT_2U`对象`CD2DPointU`构造 。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DPointU：：运算符 CPoint](#operator_cpoint)|转换为`CD2DPointU``CPoint`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dpointucd2dpointu"></a><a name="cd2dpointu"></a>CD2DPointU：CD2DPointU

从 CPoint 对象构造 CD2DPointU 对象。

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>参数

*pt*<br/>
源点

*Ux*<br/>
源 X

*uY*<br/>
源 Y

## <a name="cd2dpointuoperator-cpoint"></a><a name="operator_cpoint"></a>CD2DPointU：：运算符 CPoint

将 CD2DPointU 转换为 CPoint 对象。

```
operator CPoint();
```

### <a name="return-value"></a>返回值

D2D 点的当前值。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
