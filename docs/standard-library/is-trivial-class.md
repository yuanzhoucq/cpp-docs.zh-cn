---
title: is_trivial 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 1d218848fd65ca68022e3e66df02201582626711
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457424"
---
# <a name="istrivial-class"></a>is_trivial 类

测试类型是否为通常类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*T*是普通类型, 则类型谓词的实例为 true; 否则为 false。 常用类型是标量类型、完全可复制类类型、这些类型的数组以及这些类型的 cv 限定版本。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
