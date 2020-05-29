---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: f363e309b91e44472447d040aa36752750afec6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188930"
---
# <a name="false-c"></a>false (C++)

关键字是类型为[bool](../cpp/bool-cpp.md)的变量或条件表达式的两个值之一（条件表达式现在为**true**布尔表达式）。 例如，如果 `i` 是**bool**类型的变量，则 `i = false;` 语句将**false**分配给 `i`。

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
