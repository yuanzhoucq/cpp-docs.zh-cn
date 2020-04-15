---
title: CDefaultCharTraits 类
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 40c4d107d05e6d7b610e7c46be920d91d8fe6086
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327097"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits 类

此类提供两个静态函数，用于大写大写和大写之间的字符转换。

## <a name="syntax"></a>语法

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Cdefault 字符：：字符](#chartolower)|（静态）调用此函数以将字符转换为大写。|
|[Cdefault 字符：：字符上部](#chartoupper)|（静态）调用此函数以将字符转换为小写。|

## <a name="remarks"></a>备注

此类提供类[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)使用的函数。

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cdefaultchartraitschartolower"></a><a name="chartolower"></a>Cdefault 字符：：字符

调用此函数以将字符转换为小写。

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>参数

** x <br/>
要转换为小写的字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

## <a name="cdefaultchartraitschartoupper"></a><a name="chartoupper"></a>Cdefault 字符：：字符上部

调用此函数以将字符转换为大写。

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>参数

** x <br/>
要转换为大写的字符。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
