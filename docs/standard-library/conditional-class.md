---
title: conditional 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: b8f0f69cc1e4f6966bc9ccb63fe529436295badd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457325"
---
# <a name="conditional-class"></a>conditional 类

根据指定的条件，从两种类型之中选择其中一种。

## <a name="syntax"></a>语法

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>参数

*B*\
用于确定所选类型的值。

*T1*\
当 B 为 true 时的类型结果。

\
当 B 为 false 时的类型结果。

## <a name="remarks"></a>备注

当*b*的计算`conditional<B, T1, T2>::type`结果为**true**时, 模板成员 typedef 的计算结果为 *T1* , 而*b*的计算结果为**false**。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
