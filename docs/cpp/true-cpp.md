---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: 5cfc99f446499201a0f54c8e5b1dcc2d7152445c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404697"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>语法

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>备注

此关键字是类型的变量的两个值之一[bool](../cpp/bool-cpp.md)或条件表达式 （条件表达式现在是 true 的布尔表达式）。 如果`i`属于类型**bool**，然后语句`i = true;`分配**true**到`i`。

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

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)