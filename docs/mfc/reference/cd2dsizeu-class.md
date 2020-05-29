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
ms.openlocfilehash: a5b87fe2ddd8fb32ddbbb2884c630952afdb079c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359289"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU 类

D2D1_SIZE_U的包装。

## <a name="syntax"></a>语法

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DSizeU：CD2DSizeU](#cd2dsizeu)|已重载。 从`CD2DSizeU``D2D1_SIZE_U`对象构造对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DSizeU：：IsNull](#isnull)|返回**一个布尔值**，指示表达式是否不包含有效数据 （NULL）。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DSizeU：：运算符 CSize](#operator_csize)|转换为`CD2DSizeU``CSize`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dsizeucd2dsizeu"></a><a name="cd2dsizeu"></a>CD2DSizeU：CD2DSizeU

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

*大小*<br/>
源大小

*残雪*<br/>
源宽度

*cy*<br/>
源高度

## <a name="cd2dsizeuisnull"></a><a name="isnull"></a>CD2DSizeU：：IsNull

返回一个布尔值，指示表达式是否不包含有效数据 （Null）。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果宽度和高度为空，则为 TRUE;否则 FALSE。

## <a name="cd2dsizeuoperator-csize"></a><a name="operator_csize"></a>CD2DSizeU：：运算符 CSize

将 CD2DSizeU 转换为 CSize 对象。

```
operator CSize();
```

### <a name="return-value"></a>返回值

D2D 大小的当前值。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
