---
title: 编译器错误 C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 2bf9bd322812764b2f63493d4b22b58d853a25fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756833"
---
# <a name="compiler-error-c2001"></a>编译器错误 C2001

常量中有换行符

不能在第二行继续使用字符串常量，除非你执行以下操作：

- 用反斜杠结束第一行。

- 用双引号结束第一行的字符串，并使用另一个双引号打开下一行中的字符串。

用 \n 结束第一行是不够的。

## <a name="example"></a>示例

下面的示例生成 C2001：

```cpp
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

## <a name="example"></a>示例

行继续符后面的下一行开头的空格将包含在字符串常量中。 上面所示的示例都不会在字符串常量中嵌入一个换行符。 可以嵌入换行符，如下所示：

```cpp
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```
