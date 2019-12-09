---
title: 编译器错误 C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 83b78336d74037b9f9f52da8327479f506db1ffc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751062"
---
# <a name="compiler-error-c2015"></a>编译器错误 C2015

常量中的字符太多

字符常量包含两个以上的字符。 对于标准字符常量，长度限制为一个字符，长字符常量限制为两个字符。

转义序列（如 \t）转换为单个字符。

## <a name="example"></a>示例

下面的示例生成 C2015：

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>示例

使用 Microsoft 扩展时，也会发生 C2015，转换为整数。  下面的示例生成 C2015：

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
