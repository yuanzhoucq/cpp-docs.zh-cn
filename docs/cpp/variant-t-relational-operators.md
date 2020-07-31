---
title: _variant_t 关系运算符
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
ms.openlocfilehash: 6e0296a2bf4ce97e41fdf6208c3dd1c6b91215dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226929"
---
# <a name="_variant_t-relational-operators"></a>_variant_t 关系运算符

**Microsoft 专用**

比较两个 `_variant_t` 对象是否相等。

## <a name="syntax"></a>语法

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>参数

*varSrc*<br/>
`VARIANT`要与对象进行比较的 `_variant_t` 。

*.Psrc*<br/>
要与对象进行比较的指向的指针 `VARIANT` `_variant_t` 。

## <a name="return-value"></a>返回值

**`true`** 如果比较包含，则返回; **`false`** 否则返回。

## <a name="remarks"></a>备注

将 `_variant_t` 对象与进行比较 `VARIANT` ，测试是否相等或不相等。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_variant_t 类](../cpp/variant-t-class.md)
