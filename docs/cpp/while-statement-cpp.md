---
title: While 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 669618e9807109be18117968b1f5b6f49ec15e07
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325973"
---
# <a name="while-statement-c"></a>While 语句 (C++)

执行*语句*重复直至*表达式*计算结果为零。

## <a name="syntax"></a>语法

```
while ( expression )
   statement
```

## <a name="remarks"></a>备注

测试*表达式*发生在每次执行循环; 因此，**虽然**循环执行零次或多次。 *表达式*必须为整型类型、 指针类型或类类型明确转换为整型或指针类型。

一个**虽然**时，还可以终止循环[中断](../cpp/break-statement-cpp.md)， [goto](../cpp/goto-statement-cpp.md)，或者[返回](../cpp/return-statement-cpp.md)正文执行的语句中。 使用[继续](../cpp/continue-statement-cpp.md)终止当前迭代，而不退出**虽然**循环。 **继续**将控制传递到下一个迭代**虽然**循环。

下面的代码使用**虽然**循环，以裁剪尾随下划线从字符串：

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

终止条件计算循环的顶部。 如果不有任何尾随下划线，则循环将永远不会执行。

## <a name="see-also"></a>请参阅

[迭代语句](../cpp/iteration-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[do-while 语句 (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for 语句 (C++)](../cpp/for-statement-cpp.md)<br/>
[基于范围的 for 语句 (C++)](../cpp/range-based-for-statement-cpp.md)