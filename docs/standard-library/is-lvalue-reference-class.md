---
title: is_lvalue_reference 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: 5bcd5c8333f011475cb11a452759c8986ab22215
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456208"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference 类

测试类型是否是左值引用。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*是对某个对象或函数的引用, 则此类型谓词的实例为 true; 否则为 false。 请注意, *Ty*可能不是右值引用。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)
