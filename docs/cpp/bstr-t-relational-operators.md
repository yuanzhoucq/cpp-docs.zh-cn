---
title: _bstr_t 关系运算符
ms.date: 05/07/2019
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
helpviewer_keywords:
- _bstr_t [C++]
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
ms.openlocfilehash: 8fc163255a5ab342938f56f8a22af3984a48e56a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216617"
---
# <a name="_bstr_t-relational-operators"></a>_bstr_t 关系运算符

**Microsoft 专用**

比较两个 `_bstr_t` 对象。

## <a name="syntax"></a>语法

```
bool operator!( ) const throw( );
bool operator==(const _bstr_t& str) const throw( );
bool operator!=(const _bstr_t& str) const throw( );
bool operator<(const _bstr_t& str) const throw( );
bool operator>(const _bstr_t& str) const throw( );
bool operator<=(const _bstr_t& str) const throw( );
bool operator>=(const _bstr_t& str) const throw( );
```

## <a name="remarks"></a>备注

这些运算符按字典顺序比较两个 `_bstr_t` 对象。 **`true`** 如果比较保持，则运算符返回; 否则返回 **`false`** 。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)
