---
title: CD2DRectU 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3fc66e5cc116ce97a9abead8eeb6607f7a36ef7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052676"
---
# <a name="cd2drectu-class"></a>CD2DRectU 类

`D2D1_RECT_U`的包装器。

## <a name="syntax"></a>语法

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|已重载。 构造`CD2DRectU`对象从`D2D1_RECT_U`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|返回**布尔**值，该值指示表达式是否包含任何有效的数据 (NULL)。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DRectU::operator CRect](#operator_crect)|将转换`CD2DRectU`到`CRect`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="cd2drectu"></a>  CD2DRectU::CD2DRectU

构造 CRect 对象从一个 CD2DRectU 对象。

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

*rect*<br/>
源矩形

*uLeft*<br/>
源左边缘坐标

*uTop*<br/>
源上边缘坐标

*uRight*<br/>
源角坐标

*uBottom*<br/>
源下边缘坐标

##  <a name="isnull"></a>  CD2DRectU::IsNull

返回一个布尔值，该值指示表达式是否包含任何有效的数据 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

矩形的上、 左、 下、 和正确的值均相等，则为 0; 如果为 TRUE否则为 FALSE。

##  <a name="operator_crect"></a>  CD2DRectU::operator CRect

将 CD2DRectU 转换为 CRect 对象。

```
operator CRect();
```

### <a name="return-value"></a>返回值

D2D 矩形的当前值。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
