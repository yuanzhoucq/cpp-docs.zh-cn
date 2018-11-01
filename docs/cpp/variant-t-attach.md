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
ms.openlocfilehash: 510267c7ab00fe22a93dc01342def5fc262ddb04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435069"
---
# <a name="varianttattach"></a>_variant_t::Attach

**Microsoft 专用**

将附加`VARIANT`对象插入 **_variant_t**对象。

## <a name="syntax"></a>语法

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>参数

*varSrc*<br/>
一个`VARIANT`要附加到此对象 **_variant_t**对象。

## <a name="remarks"></a>备注

取得所有权的`VARIANT`通过封装。 此成员函数将释放所有现有封装`VARIANT`，然后复制提供`VARIANT`，并设置其`VARTYPE`为 VT_EMPTY 以确保其资源可以仅由发布 **_variant_t**析构函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_variant_t 类](../cpp/variant-t-class.md)