---
title: 编译器错误 C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: ca9e2d272a5e9ab8fd69094bc1633dbd6ea2c3e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624687"
---
# <a name="compiler-error-c3498"></a>编译器错误 C3498

var： 无法捕获具有托管的变量或 WinRTtype

无法在 lambda 中捕获具有托管类型或 Windows 运行时类型的变量。

### <a name="to-correct-this-error"></a>更正此错误

- 将托管或 Windows 运行时变量传递到 lambda 表达式的参数列表。

## <a name="example"></a>示例

下面的示例将生成 C3498，因为 lambda 表达式的捕获列表中出现了具有托管类型的变量：

```
// C3498a.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [&s](String ^ r)
      { return String::Concat(s, r); } (", World!"); // C3498
}
```

## <a name="example"></a>示例

下面的示例通过将托管变量 `s` 传递到 lambda 表达式的参数列表，解决了 C3498：

```
// C3498b.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [](String ^ s, String ^ r)
      { return String::Concat(s, r); } (s, ", World!");
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)