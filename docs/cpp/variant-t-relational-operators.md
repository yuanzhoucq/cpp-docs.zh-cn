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
ms.openlocfilehash: e0d7ea1a0bcaf8329cff0cdfb0c01154f3c5a73b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187565"
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

#### <a name="parameters"></a>parameters

*varSrc*<br/>
要与 `_variant_t` 对象进行比较的 `VARIANT`。

*.Psrc*<br/>
指向要与 `_variant_t` 对象进行比较的 `VARIANT` 的指针。

## <a name="return-value"></a>返回值

如果比较保持，则返回**true** ，否则返回**false** 。

## <a name="remarks"></a>备注

将 `_variant_t` 对象与 `VARIANT`进行比较，测试是否相等或不相等。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_variant_t 类](../cpp/variant-t-class.md)
