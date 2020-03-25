---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: b0692c9befaa6b7e787ada624dcbb56b074c9f9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160458"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Microsoft 专用**

将 `_variant_t` 对象的类型更改为指示的 `VARTYPE`。

## <a name="syntax"></a>语法

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>parameters

*vartype*<br/>
此 `_variant_t` 对象的 `VARTYPE`。

*.Psrc*<br/>
指向要转换的 `_variant_t` 对象的指针。 如果此值为 NULL，则转换就地执行。

## <a name="remarks"></a>备注

此成员函数将 `_variant_t` 对象转换为指示的 `VARTYPE`。 如果 *.psrc*为 NULL，则会就地执行转换，否则，将从 *.psrc*中复制此 `_variant_t` 对象，然后转换。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_variant_t 类](../cpp/variant-t-class.md)
