---
title: is_trivially_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: 11aed7fbe2540984d8ed69f88b2a95649e8fee70
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457496"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable 类

测试 `From` 类型的值是否能够普通赋予 `To` 类型

## <a name="syntax"></a>语法

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>参数

*自*\
接收赋值的对象的类型。

*从*\
提供值的对象的类型。

## <a name="remarks"></a>备注

表达式 `declval<To>() = declval<From>()` 必须格式正确，且编译器必须已知其不需要任何重要操作。 和必须是完整的类型、void 或未知绑定的数组。  `From` `To`

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
