---
title: While 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 168b1fc20d165c44c3230a8d1094c99b689ddbb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233543"
---
# <a name="while-statement-c"></a>While 语句 (C++)

重复执行*语句*，直到*expression*的计算结果为零。

## <a name="syntax"></a>语法

```
while ( expression )
   statement
```

## <a name="remarks"></a>备注

*表达式*的测试在每次执行循环之前发生;因此， **`while`** 循环将执行零次或多次。 *表达式*的类型必须为整型、指针类型或类类型，且该类型具有到整数或指针类型的明确转换。

**`while`** 当执行语句体中的[break](../cpp/break-statement-cpp.md)、 [goto](../cpp/goto-statement-cpp.md)或[return](../cpp/return-statement-cpp.md)时，循环也可以终止。 使用 "[继续](../cpp/continue-statement-cpp.md)" 可在不退出循环的情况下终止当前迭代 **`while`** 。 **`continue`** 将控制传递到循环的下一次迭代 **`while`** 。

下面的代码使用 **`while`** 循环来剪裁字符串中的尾随下划线：

```cpp
// while_statement.cpp

#include <string.h>
#include <stdio.h>
char *trim( char *szSource )
{
    char *pszEOS = 0;

    //  Set pointer to character before terminating NULL
    pszEOS = szSource + strlen( szSource ) - 1;

    //  iterate backwards until non '_' is found
    while( (pszEOS >= szSource) && (*pszEOS == '_') )
        *pszEOS-- = '\0';

    return szSource;
}
int main()
{
    char szbuf[] = "12345_____";

    printf_s("\nBefore trim: %s", szbuf);
    printf_s("\nAfter trim: %s\n", trim(szbuf));
}
```

终止条件在循环的顶部进行评估。 如果没有尾随下划线，则循环永远不会执行。

## <a name="see-also"></a>另请参阅

[迭代语句](../cpp/iteration-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[do-while 语句 (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for 语句（c + +）](../cpp/for-statement-cpp.md)<br/>
[基于范围的 for 语句 (C++)](../cpp/range-based-for-statement-cpp.md)
