---
title: 编译器错误 C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 50a06180dabfa192292fae7ba1962b6b7455bb89
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024019"
---
# <a name="compiler-error-c3537"></a>编译器错误 C3537

type： 不能转换为包含 auto 的类型

不能转换为指定的类型的变量，因为该类型包含`auto`关键字和默认[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项。

## <a name="example"></a>示例

下面的代码会产生 C3537，因为变量将转换为包含的类型`auto`关键字。

```
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)