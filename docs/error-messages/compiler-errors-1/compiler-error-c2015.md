---
title: 编译器错误 C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: d761dfde26cce9c99ccd4c3e6fd86ae1d6e16ddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351087"
---
# <a name="compiler-error-c2015"></a>编译器错误 C2015

常量中的字符太多

字符常量包含两个以上的字符。 限制为一个字符作为标准字符常量和两个字符长字符常数。

转义序列，如 \t，转换为单个字符。

## <a name="example"></a>示例

下面的示例生成 C2015:

```
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>示例

使用 Microsoft 扩展，转换为整数字符常量时，也可能发生 C2015。  下面的示例生成 C2015:

```
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```