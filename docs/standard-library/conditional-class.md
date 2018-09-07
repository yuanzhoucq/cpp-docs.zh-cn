---
title: conditional 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a553c2975dd5a58673bd4caa6e7c9ba25d33183
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106608"
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
