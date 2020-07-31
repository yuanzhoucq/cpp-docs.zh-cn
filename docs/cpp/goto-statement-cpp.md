---
title: goto 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: e56ebfadea0d643ac68e2ace722a39587bd01312
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223702"
---
# <a name="goto-statement-c"></a>goto 语句 (C++)

**`goto`** 语句无条件地将控制转移到由指定标识符标记的语句。

## <a name="syntax"></a>语法

```
goto identifier;
```

## <a name="remarks"></a>备注

由 `identifier` 指定的标记语句必须位于当前函数中。 所有 `identifier` 名称都是内部命名空间的成员，因此不会干扰其他标识符。

语句标签仅对语句有意义 **`goto`** ; 否则，将忽略语句标签。 不能重新声明标签。

**`goto`** 不允许语句将控制转移到跳过初始化该位置范围内的任何变量的位置。 下面的示例引发 C2362：

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

**`break`** 如果可能，使用、 **`continue`** 和 **`return`** 语句而不是语句，是一种很好的编程风格 **`goto`** 。 但是，由于 **`break`** 语句只从循环的一个级别退出，因此您可能必须使用 **`goto`** 语句退出深度嵌套的循环。

有关标签和语句的详细信息 **`goto`** ，请参阅[标记的语句](../cpp/labeled-statements.md)。

## <a name="example"></a>示例

在此示例中， **`goto`** 语句将控制权转交给标记为 `stop` `i` 等于3的点。

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>另请参阅

[跳转语句](../cpp/jump-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
