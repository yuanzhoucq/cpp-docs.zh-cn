---
title: CD2DEllipse 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
dev_langs:
- C++
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93fc2b788d450b591ebd20be49f25133c95f22b6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052838"
---
# <a name="cd2dellipse-class"></a>CD2DEllipse 类

`D2D1_ELLIPSE`的包装器。

## <a name="syntax"></a>语法

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|已重载。 构造`CD2DEllipse`对象从`D2D1_ELLIPSE`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="cd2dellipse"></a>  CD2DEllipse::CD2DEllipse

构造 CD2DRectF 对象从一个 CD2DEllipse 对象。

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
  CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>参数

*rect*<br/>
源矩形

*椭圆*<br/>
源椭圆

*ptCenter*<br/>
椭圆的中心点。

*sizeRadius*<br/>
X 轴半径和 Y 轴半径的椭圆。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
