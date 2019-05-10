---
title: 编译器错误 C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 03b54fe2373063c8c0f9905da93822928392998d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209018"
---
# <a name="compiler-error-c2001"></a>编译器错误 C2001

常量中有换行符

一个字符串常量不能继续第二个行上，除非你执行以下操作：

- 结束，第一行用反斜杠。

- 结束的字符串与双引号匹配的第一行上，打开在下一行中的字符串与另一个双引号。

结束，第一行用 \n 是不够的。

## <a name="example"></a>示例

下面的示例生成 C2001:

```
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

字符串常量中包括空格开头的行继续符后的下一行。 如上所示的示例都没有嵌入字符串常量中换行字符。 您可以嵌入换行字符，如下所示：

```
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