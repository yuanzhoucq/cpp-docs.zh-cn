---
title: CD2DSizeF 类
ms.date: 11/04/2016
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: 09ccd8c4ba6bb0c345adb32bcf22686c485d1184
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296587"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF 类

D2D1_SIZE_F 包装器。

## <a name="syntax"></a>语法

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|已重载。 构造`CD2DSizeF`对象从`D2D1_SIZE_F`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|返回**布尔**值，该值指示表达式是否包含任何有效的数据 (NULL)。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DSizeF::operator CSize](#operator_csize)|将转换`CD2DSizeF`到`CSize`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF

构造 CSize 对象从一个 CD2DSizeF 对象。

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
  CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>参数

*size*<br/>
源大小

*cx*<br/>
源宽度

*cy*<br/>
源高度

##  <a name="isnull"></a>  CD2DSizeF::IsNull

返回一个布尔值，该值指示表达式是否包含任何有效的数据 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果宽度和高度都为空; 则为 TRUE否则为 FALSE。

##  <a name="operator_csize"></a>  CD2DSizeF::operator CSize

将 CD2DSizeF 转换为 CSize 对象。

```
operator CSize();
```

### <a name="return-value"></a>返回值

D2D 大小的当前值。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
