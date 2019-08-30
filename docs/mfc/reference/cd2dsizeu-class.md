---
title: CD2DSizeU 类
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: 45625331d0c1be8ca7c663d12c53516dc7bd77c7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177186"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU 类

D2D1_SIZE_U 的包装器。

## <a name="syntax"></a>语法

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|已重载。 `CD2DSizeU` 从`D2D1_SIZE_U`对象构造对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DSizeU::IsNull](#isnull)|返回一个**布尔**值, 该值指示表达式是否不包含有效数据 (NULL)。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DSizeU:: operator CSize](#operator_csize)|转换`CD2DSizeU` 为`CSize`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>要求

**标头:** afxrendertarget

##  <a name="cd2dsizeu"></a>CD2DSizeU:: CD2DSizeU

从 CSize 对象构造 CD2DSizeU 对象。

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>参数

*size*<br/>
源大小

*cx*<br/>
源宽度

*cy*<br/>
源高度

##  <a name="isnull"></a>CD2DSizeU:: IsNull

返回一个布尔值, 该值指示表达式是否不包含有效数据 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果 "宽度" 和 "高度" 为空, 则为 TRUE;否则为 FALSE。

##  <a name="operator_csize"></a>CD2DSizeU:: operator CSize

将 CD2DSizeU 转换为 CSize 对象。

```
operator CSize();
```

### <a name="return-value"></a>返回值

D2D 大小的当前值。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
