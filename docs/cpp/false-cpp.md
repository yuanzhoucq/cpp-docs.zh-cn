---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: d6162bdde3dea0d245a0c83c1d52b06003fee16c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227486"
---
# <a name="false-c"></a>false (C++)

关键字是类型为[bool](../cpp/bool-cpp.md)的变量或条件表达式（条件表达式现在为布尔表达式）的两个值之一 **`true`** 。 例如，如果 `i` 是类型为的变量 **`bool`** ，则该 `i = false;` 语句将分配 **`false`** 给 `i` 。

## <a name="example"></a>示例

```cpp
// bool_false.cpp
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
