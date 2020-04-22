---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 60ad1c1bd95eb35f2a4f2800f79d0326c68a1176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745849"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**微软特定**

将字符串分配给此 `_variant_t` 对象。

## <a name="syntax"></a>语法

```cpp
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>参数

*pSrc*<br/>
指向字符串的指针。

## <a name="remarks"></a>备注

将 ANSI 字符串转换为 Unicode `BSTR` 字符串并将其分配给此 `_variant_t` 对象。

**结束微软特定**

## <a name="see-also"></a>请参阅

[_variant_t类](../cpp/variant-t-class.md)
