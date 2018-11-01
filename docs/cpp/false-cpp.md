---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: 5fc27c7f1dfde7d1f686f0a752652773ade9cc0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464059"
---
# <a name="false-c"></a>false (C++)

关键字是类型的变量的两个值之一[bool](../cpp/bool-cpp.md)或条件表达式 (条件表达式现**true**布尔表达式)。 例如，如果`i`类型的变量**bool**，则`i = false;`语句分配**false**到`i`。

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

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)