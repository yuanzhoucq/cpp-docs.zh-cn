---
title: is_move_constructible 类
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 9585a932a34a24769201aaa379525a9b4c181e41
ms.sourcegitcommit: 33a898bf976c65f998b4e88a84765a0cef4193a8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920091"
---
# <a name="is_move_constructible-class"></a>is_move_constructible 类

测试是否可以使用移动操作构造该类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>参数

*T* \
要计算的类型。

## <a name="remarks"></a>备注

如果可以使用移动操作构造类型*T* ，则其计算结果为**true**的类型谓词。 此谓词等效于 `is_constructible<T, T&&>`。 不具有移动构造函数的类型*T* ，但具有接受 `const T&` 参数的复制构造函数，满足 `std::is_move_constructible`。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
