---
title: aligned_union 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: ae6ef629535238b9406216afd9f680a5c1e1afe0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623790"
---
# <a name="aligned_union-class"></a>aligned_union 类

提供足够大并适当对齐的 POD 类型，以存储所需大小的联合类型。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>参数

*长度*\
联合中的最大类型的对齐值。

*各种*\
基础联合中的不同类型。

## <a name="remarks"></a>备注

使用类模板获取在未初始化的存储中存储联合所需的对齐方式和大小。 成员 typedef 将 `type` POD 类型命名为适用于*类型*中列出的任何类型的存储; 最小大小为*Len*。 类型的静态成员 `alignment_value` `std::size_t` 包含*类型*中列出的所有类型所需的最严格对齐。

## <a name="example"></a>示例

以下示例演示如何使用 `aligned_union` 来分配对齐的堆栈缓冲区以放置联合。

```cpp
// std__type_traits__aligned_union.cpp
#include <iostream>
#include <type_traits>

union U_type
{
    int i;
    float f;
    double d;
    U_type(float e) : f(e) {}
};

typedef std::aligned_union<16, int, float, double>::type aligned_U_type;

int main()
{
    // allocate memory for a U_type aligned on a 16-byte boundary
    aligned_U_type au;
    // do placement new in the aligned memory on the stack
    U_type* u = new (&au) U_type(1.0f);
    if (nullptr != u)
    {
        std::cout << "value of u->i is " << u->i << std::endl;
        // must clean up placement objects manually!
        u->~U_type();
    }
}
```

```Output
value of u->i is 1065353216
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](type-traits.md)\
[alignment_of 类](alignment-of-class.md)
