---
title: CD2DSizeF 类
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: be050f98855e5af794166e1f86962111a23bfa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369068"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF 类

D2D1_SIZE_F的包装。

## <a name="syntax"></a>语法

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DSizeF：CD2DSizeF](#cd2dsizef)|已重载。 从`CD2DSizeF``D2D1_SIZE_F`对象构造对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DSizeF：：IsNull](#isnull)|返回**一个布尔值**，指示表达式是否不包含有效数据 （NULL）。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DSizeF：：运算符 CSize](#operator_csize)|转换为`CD2DSizeF``CSize`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dsizefcd2dsizef"></a><a name="cd2dsizef"></a>CD2DSizeF：CD2DSizeF

从 CSize 对象构造 CD2DSizeF 对象。

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>参数

*大小*<br/>
源大小

*残雪*<br/>
源宽度

*cy*<br/>
源高度

## <a name="cd2dsizefisnull"></a><a name="isnull"></a>CD2DSizeF：：IsNull

返回一个布尔值，指示表达式是否不包含有效数据 （Null）。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果宽度和高度为空，则为 TRUE;否则 FALSE。

## <a name="cd2dsizefoperator-csize"></a><a name="operator_csize"></a>CD2DSizeF：：运算符 CSize

将 CD2DSizeF 转换为 CSize 对象。

```
operator CSize();
```

### <a name="return-value"></a>返回值

D2D 大小的当前值。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
