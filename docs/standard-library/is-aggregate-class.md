---
title: is_aggregate 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 89749e2b4c0e6aaf00de074718cfb598333bc739
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456696"
---
# <a name="isaggregate-class"></a>is_aggregate 类

测试类型是否是标记为 `aggregate` 的类类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_aggregate;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*T*是标记`aggregate`为的类类型, 则类型谓词的实例为 true; 否则为 false。 如果*T*是类类型, 则它必须是完整类型。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
