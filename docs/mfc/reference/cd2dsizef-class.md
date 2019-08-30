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
ms.openlocfilehash: df895c278003e2c71f37a00af6bf14912756701a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177201"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF 类

D2D1_SIZE_F 的包装器。

## <a name="syntax"></a>语法

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|已重载。 `CD2DSizeF` 从`D2D1_SIZE_F`对象构造对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|返回一个**布尔**值, 该值指示表达式是否不包含有效数据 (NULL)。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DSizeF:: operator CSize](#operator_csize)|转换`CD2DSizeF` 为`CSize`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>要求

**标头:** afxrendertarget

##  <a name="cd2dsizef"></a>CD2DSizeF:: CD2DSizeF

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

*size*<br/>
源大小

*cx*<br/>
源宽度

*cy*<br/>
源高度

##  <a name="isnull"></a>CD2DSizeF:: IsNull

返回一个布尔值, 该值指示表达式是否不包含有效数据 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果 "宽度" 和 "高度" 为空, 则为 TRUE;否则为 FALSE。

##  <a name="operator_csize"></a>CD2DSizeF:: operator CSize

将 CD2DSizeF 转换为 CSize 对象。

```
operator CSize();
```

### <a name="return-value"></a>返回值

D2D 大小的当前值。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
