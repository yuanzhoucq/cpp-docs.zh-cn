---
title: vector&lt;bool&gt;::reference::operator bool
ms.date: 11/04/2016
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
ms.openlocfilehash: ca2d21a7706248cd84ca3591eb717e4081972f9c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452124"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

提供从`vector<bool>::reference`到**bool**的隐式转换。

## <a name="syntax"></a>语法

```cpp
operator bool() const;
```

## <a name="return-value"></a>返回值

[vector\<bool>](../standard-library/vector-bool-class.md) 对象元素的布尔值。

## <a name="remarks"></a>备注

`vector<bool>` 对象无法通过此运算符修改。

## <a name="requirements"></a>要求

**标头：** \<vector>

**命名空间：** std

## <a name="see-also"></a>请参阅

[vector\<bool>::reference 类](../standard-library/vector-bool-reference-class.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
