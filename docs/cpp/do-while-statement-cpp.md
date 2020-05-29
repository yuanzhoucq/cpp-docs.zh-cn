---
title: do-while 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: f52c065210a8861dc065508248a506770b039b1d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189268"
---
# <a name="do-while-statement-c"></a>do-while 语句 (C++)

重复执行*语句*，直到指定的终止条件（*表达式*）的计算结果为零。

## <a name="syntax"></a>语法

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>备注

终止条件的测试在每次执行循环之后进行;因此， **do**循环会执行一次或多次，具体取决于终止表达式的值。 **do-while** 语句还可在语句体中执行 [break](../cpp/break-statement-cpp.md)、[goto](../cpp/goto-statement-cpp.md) 或 [return](../cpp/return-statement-cpp.md) 语句时终止。

*expression*必须具有算法或指针类型。 执行过程如下所示：

1. 执行语句体。

1. 接着，计算 expression。 如果 expression 为 false，则 do-while 语句将终止，控制权将传递到程序中的下一条语句。 如果 expression 为 true（非零），则将从第 1 步开始重复此过程。

## <a name="example"></a>示例

下面的示例演示了**do**语句：

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>请参阅

[迭代语句](../cpp/iteration-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[While 语句 (C++)](../cpp/while-statement-cpp.md)<br/>
[for 语句 (C++)](../cpp/for-statement-cpp.md)<br/>
[基于范围的 for 语句 (C++)](../cpp/range-based-for-statement-cpp.md)
