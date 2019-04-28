---
title: conditional 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: be81a1bc32f2f86f1d79970868933bddb8dc3620
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212100"
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

*B*<br/>
用于确定所选类型的值。

T1<br/>
当 B 为 true 时的类型结果。

T2<br/>
当 B 为 false 时的类型结果。

## <a name="remarks"></a>备注

模板成员 typedef`conditional<B, T1, T2>::type`计算结果为*T1*时*B*的计算结果为**true**，并计算结果为*T2*时*B*计算结果为**false**。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
