---
title: alignment_of 类
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 5a90f481c33431d92f0f28405e6226863d2b3913
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205010"
---
# <a name="alignment_of-class"></a>alignment_of 类

获取指定类型的对齐方式。 此结构以的形式实现 [`alignof`](../cpp/alignment-cpp-declarations.md) 。 **`alignof`** 当只需查询对齐值时，直接使用。 `alignment_of`需要整数常量时（例如在执行标记调度时），请使用。

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

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[`<type_traits>`](type-traits.md)\
[`aligned_storage`班级](aligned-storage-class.md)
