---
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: 3792ed4d0fcd86c4a4e846771c450413fda130b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187760"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Microsoft 专用**

将 `VARIANT` 对象附加到 **_variant_t**对象中。

## <a name="syntax"></a>语法

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>parameters

*varSrc*<br/>
要附加到此 **_variant_t**对象的 `VARIANT` 对象。

## <a name="remarks"></a>备注

通过封装 `VARIANT` 获取其所有权。 此成员函数将释放任何现有的封装 `VARIANT`，然后复制提供的 `VARIANT`，并将其 `VARTYPE` 设置为 VT_EMPTY，以确保其资源只能由 **_variant_t**析构函数释放。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_variant_t 类](../cpp/variant-t-class.md)
