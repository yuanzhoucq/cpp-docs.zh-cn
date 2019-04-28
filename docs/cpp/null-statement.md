---
title: Null 语句
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
ms.openlocfilehash: 2797937b184bebe0e29f8e5eae428f601c824811
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245175"
---
# <a name="null-statement"></a>Null 语句

"Null 语句"是的表达式语句*表达式*缺失。 当语言的语法调用语句而不是表达式计算时，它很有用。   它包括分号。

Null 语句通常用作迭代语句中的占位符或用作在复合语句或函数的末尾放置标签的语句。

以下代码片段说明如何将一个字符串复制到另一个字符串，并包含 null 语句：

```cpp
// null_statement.cpp
char *myStrCpy( char *Dest, const char *Source )
{
    char *DestStart = Dest;

    // Assign value pointed to by Source to
    // Dest until the end-of-string 0 is
    // encountered.
    while( *Dest++ = *Source++ )
        ;   // Null statement.

    return DestStart;
}

int main()
{
}
```

## <a name="see-also"></a>请参阅

[表达式语句](../cpp/expression-statement.md)