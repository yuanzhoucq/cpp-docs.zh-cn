---
title: is_lvalue_reference 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: e032522e790b7027886ba1a6199ed7fdf86c0936
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351938"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference 类

测试类型是否是左值引用。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

此类型谓词的实例保留为 true 如果类型*Ty*是对某个对象或函数，否则为 false 的引用。 请注意， *Ty*可能右值引用。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
