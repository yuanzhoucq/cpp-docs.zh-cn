---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: f6420d0abea8bac1d385c1cfdfd58a5500cf5bd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185835"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>语法

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>备注

此关键字是类型为[bool](../cpp/bool-cpp.md)的变量或条件表达式（条件表达式现在为 true 布尔表达式）的两个值之一。 如果 `i` 的类型为 **`bool`** ，则语句将 `i = true;` 分配 **`true`** 给 `i` 。

## <a name="example"></a>示例

```cpp
// bool_true.cpp
#include <stdio.h>
int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)
