---
title: is_trivially_move_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: 324e4a1f1bd3528f09f21c5e485ac814038b7517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448371"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable 类

测试类型是否具有普通移动赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*是具有普通移动赋值运算符的类, 则类型谓词的实例为 true; 否则为 false。

如果以下情况, *Ty*类的移动赋值运算符是普通运算符:

它被隐式提供

类*Ty*没有虚函数

类*Ty*没有虚拟基

类类型的所有非静态数据成员的类具有普通移动赋值运算符

类的类型数组的所有非静态数据成员的类具有普通移动赋值运算符

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
