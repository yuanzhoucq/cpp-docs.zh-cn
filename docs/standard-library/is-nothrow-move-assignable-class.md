---
title: is_nothrow_move_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_move_assignable
helpviewer_keywords:
- is_nothrow_move_assignable
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
ms.openlocfilehash: 8273be92a9c7e60e446b3c2b561a6020e70fb2f2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455894"
---
# <a name="isnothrowmoveassignable-class"></a>is_nothrow_move_assignable 类

测试类型是否具有 **nothrow** 移动赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*具有 nothrow 移动赋值运算符, 则类型谓词的实例为 true; 否则为 false。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
