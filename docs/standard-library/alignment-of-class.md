---
title: alignment_of 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 5222e70965db69d33ec62039bf9013a52d145705
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456448"
---
# <a name="alignmentof-class"></a>alignment_of 类

获取指定类型的对齐方式。 此结构根据 [alignof](../cpp/alignof-and-alignas-cpp.md) 来实现。 只需查询对齐方式值时可直接使用 `alignof`。 需要整数常量时（例如在执行标记调度时），可使用 alignment_of。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

类型查询保存类型*Ty*的对齐方式的值。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[aligned_storage 类](../standard-library/aligned-storage-class.md)
