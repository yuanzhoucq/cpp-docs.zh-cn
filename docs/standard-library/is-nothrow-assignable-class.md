---
title: is_nothrow_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 7130079ff58820ec5a8893fd248c5b98fc10c93c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222363"
---
# <a name="is_nothrow_assignable-class"></a>is_nothrow_assignable 类

测试*从*类型的值是否可以分配*给类型，* 以及是否已知不引发赋值。

## <a name="syntax"></a>语法

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>参数

*自*\
接收赋值的对象的类型。

*从*\
提供值的对象的类型。

## <a name="remarks"></a>备注

表达式 `declval<To>() = declval<From>()` 必须格式正确，编译器必须已知此表达式不会引发。 *From*和*To*都必须是完整类型、 **`void`** 或未知绑定的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)
