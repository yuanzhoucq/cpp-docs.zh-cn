---
title: is_rvalue_reference 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_rvalue_reference
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
ms.openlocfilehash: 58cbf5709eda4f41d2edab7ddac1e0a04a9c74cf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455672"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference 类

测试类型是否是右值引用。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*是[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md), 则此类型谓词的实例为 true。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)
