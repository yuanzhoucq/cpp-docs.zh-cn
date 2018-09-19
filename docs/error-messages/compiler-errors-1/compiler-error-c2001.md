---
title: 编译器错误 C2001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71048a706678e4d9e6906972ebf148748927e829
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088237"
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