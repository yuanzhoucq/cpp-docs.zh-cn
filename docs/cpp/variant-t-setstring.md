---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: d07e995be0ecd99974356a7516e7c4deee677637
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628236"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Microsoft 专用**

将字符串分配给此 `_variant_t` 对象。

## <a name="syntax"></a>语法

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>参数

*pSrc*<br/>
指向字符串的指针。

## <a name="remarks"></a>备注

将 ANSI 字符串转换为 Unicode `BSTR` 字符串并将其分配给此 `_variant_t` 对象。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_variant_t 类](../cpp/variant-t-class.md)