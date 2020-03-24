---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 0cd300a09c29668c496d93109d1bc862947e948c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187552"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Microsoft 专用**

将字符串分配给此 `_variant_t` 对象。

## <a name="syntax"></a>语法

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>parameters

*.Psrc*<br/>
指向字符串的指针。

## <a name="remarks"></a>备注

将 ANSI 字符串转换为 Unicode `BSTR` 字符串并将其分配给此 `_variant_t` 对象。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_variant_t 类](../cpp/variant-t-class.md)
