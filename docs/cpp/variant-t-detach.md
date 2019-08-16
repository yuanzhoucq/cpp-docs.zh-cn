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
ms.openlocfilehash: 8426c80af04b2c0906af150ea3e91304335e9f69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500564"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Microsoft 专用**

从此对象分离`VARIANT`封装的对象。`_variant_t`

## <a name="syntax"></a>语法

```
VARIANT Detach( );
```

## <a name="return-value"></a>返回值

封装`VARIANT`的。

## <a name="remarks"></a>备注

提取并返回封装`VARIANT`的, 然后清除此`_variant_t`对象而不销毁它。 此成员函数`VARIANT`从封装中移除, 并`VARTYPE`将此`_variant_t`对象的设置为 VT_EMPTY。 通过调用`VARIANT` [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)函数, 可以释放返回的。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_variant_t 类](../cpp/variant-t-class.md)