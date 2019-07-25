---
title: is_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: 33b0ce6112119c935ff70e5d619b284acc6ee8c2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456672"
---
# <a name="isassignable-class"></a>is_assignable 类

测试 `From` 类型的值是否可以分配给 `To` 类型。

## <a name="syntax"></a>语法

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>参数

*自*\
接收赋值的对象的类型。

*从*\
提供值的对象的类型。

## <a name="remarks"></a>备注

未计算的表达式 `declval<To>() = declval<From>()` 必须具有正确格式。 和必须是完整的类型、void 或未知绑定的数组。  `From` `To`

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
