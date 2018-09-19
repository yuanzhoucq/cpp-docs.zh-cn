---
title: _variant_t::Detach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs:
- C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab1e4f83025dcc3e4bc65274746e0617cf31b5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065018"
---
# <a name="varianttdetach"></a>_variant_t::Detach

**Microsoft 专用**

分离封装`VARIANT`从此对象`_variant_t`对象。

## <a name="syntax"></a>语法

```
VARIANT Detach( );
```

## <a name="return-value"></a>返回值

封装`VARIANT`。

## <a name="remarks"></a>备注

提取并返回封装`VARIANT`，然后清除此`_variant_t`对象而不销毁它。 此成员函数将移除`VARIANT`从封装和集`VARTYPE`此`_variant_t`对象为 VT_EMPTY。 由您来释放返回`VARIANT`通过调用[VariantClear](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantclear)函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_variant_t 类](../cpp/variant-t-class.md)