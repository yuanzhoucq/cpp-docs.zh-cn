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
ms.openlocfilehash: d0822dfc730cbbb64f8364e6fa8fe8bc7207f9f9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750738"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**微软特定**

将`VARIANT`对象附加到 **_variant_t**对象。

## <a name="syntax"></a>语法

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>参数

*varSrc*<br/>
要`VARIANT`附加到此 **_variant_t**对象的对象。

## <a name="remarks"></a>备注

通过封装获取`VARIANT`的所有权。 此成员函数释放任何现有的`VARIANT`封装，然后复制提供的`VARIANT`，并将其`VARTYPE`设置到VT_EMPTY以确保其资源只能由 **_variant_t**析构函数释放。

**结束微软特定**

## <a name="see-also"></a>请参阅

[_variant_t类](../cpp/variant-t-class.md)
