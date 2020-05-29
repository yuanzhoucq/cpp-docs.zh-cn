---
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 9737db6b77483fa55e1dad90b9464752cd8537a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187734"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Microsoft 专用**

从此 `_variant_t` 对象分离封装的 `VARIANT` 对象。

## <a name="syntax"></a>语法

```
VARIANT Detach( );
```

## <a name="return-value"></a>返回值

封装的 `VARIANT`。

## <a name="remarks"></a>备注

提取并返回封装的 `VARIANT`，然后清除此 `_variant_t` 对象而不销毁它。 此成员函数从封装中移除 `VARIANT`，并将此 `_variant_t` 对象的 `VARTYPE` 设置为 VT_EMPTY。 通过调用[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)函数，可以释放返回的 `VARIANT`。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_variant_t 类](../cpp/variant-t-class.md)
