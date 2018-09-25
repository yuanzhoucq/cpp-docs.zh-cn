---
title: CD2DSizeU 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06008a2826a2ba2d358fcf3469b8a6b5b107e6be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412348"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU 类

D2D1_SIZE_U 包装器。

## <a name="syntax"></a>语法

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|已重载。 构造`CD2DSizeU`对象从`D2D1_SIZE_U`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DSizeU::IsNull](#isnull)|返回**布尔**值，该值指示表达式是否包含任何有效的数据 (NULL)。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DSizeU::operator CSize](#operator_csize)|将转换`CD2DSizeU`到`CSize`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="cd2dsizeu"></a>  CD2DSizeU::CD2DSizeU

构造 CSize 对象中的 CD2DSizeU 对象。

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

##  <a name="isnull"></a>  CD2DSizeU::IsNull

返回一个布尔值，该值指示表达式是否包含任何有效的数据 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>返回值

如果宽度和高度都为空; 则为 TRUE否则为 FALSE。

##  <a name="operator_csize"></a>  CD2DSizeU::operator CSize

将转换为 CSize 对象的 CD2DSizeU。

```
operator CSize();
```

### <a name="return-value"></a>返回值

D2D 大小的当前值。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
