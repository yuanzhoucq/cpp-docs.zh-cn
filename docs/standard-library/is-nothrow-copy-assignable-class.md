---
title: is_nothrow_copy_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: 330c97cd945e161d2bf47deb377dd732bf53b3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455977"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable 类

测试类型是否具有编译器已知不会引发的复制赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

类型谓词的实例适用于可引用类型*T* , 其中`is_nothrow_assignable<T&, const T&>`保留为 true; 否则为 false。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_nothrow_assignable 类](../standard-library/is-nothrow-assignable-class.md)
