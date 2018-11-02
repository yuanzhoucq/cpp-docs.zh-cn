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
ms.openlocfilehash: 8ea73da76f079359a4fc0250cacf70d10b545038
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660823"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits 类

此类提供两个静态函数转换为大写和小写字母之间的字符。

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

|名称|描述|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|（静态）调用此函数可将字符转换为大写。|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|（静态）调用此函数可将字符转换为小写。|

## <a name="remarks"></a>备注

此类提供了函数所使用的类[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower

调用此函数可将字符转换为小写。

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>参数

*x*<br/>
要转换为小写的字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper

调用此函数可将字符转换为大写。

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>参数

*x*<br/>
要转换为大写的字符。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
