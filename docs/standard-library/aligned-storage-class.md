---
title: aligned_storage 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_storage
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
ms.openlocfilehash: 741106888cdab63a75e090e860269f125c35efa6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623835"
---
# <a name="aligned_storage-class"></a>aligned_storage 类

生成适当对齐的类型。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Len, std::size_t Align>
struct aligned_storage;

template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>
using aligned_storage_t = typename aligned_storage<Len, Align>::type;
```

### <a name="parameters"></a>参数

*长度*\
对象大小。

*垂直*\
对象对齐方式。

## <a name="remarks"></a>备注

模板成员 typedef `type` 是具有对齐方式和大小*长度*的 POD 类型*Align*的同义词。 *Align* `alignment_of<T>::value` 对于某一类型，Align 必须等于 `T` 或为默认对齐方式。

## <a name="example"></a>示例

```cpp
#include <type_traits>
#include <iostream>

typedef std::aligned_storage<sizeof (int),
    std::alignment_of<double>::value>::type New_type;
int main()
    {
    std::cout << "alignment_of<int> == "
        << std::alignment_of<int>::value << std::endl;
    std::cout << "aligned to double == "
        << std::alignment_of<New_type>::value << std::endl;

    return (0);
    }
```

```Output
alignment_of<int> == 4
aligned to double == 8
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](type-traits.md)\
[alignment_of 类](alignment-of-class.md)
