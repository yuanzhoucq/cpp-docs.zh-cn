---
title: 编译器错误 C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: 12f50e48fc18fc23d078b6dbc7d21d05efa06d43
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032922"
---
# <a name="compiler-error-c3491"></a>编译器错误 C3491

“var”：不能在非可变 lambda 中修改按值捕获

非可变 lambda 表达式不能修改通过值捕获的变量的值。

### <a name="to-correct-this-error"></a>更正此错误

- 用 `mutable` 关键字声明 lambda 表达式，或者

- 将该变量按引用传递到 lambda 表达式的捕获列表。

## <a name="example"></a>示例

下面的示例生成 C3491，因为非可变 lambda 表达式的主体修改了捕获变量 `m`：

```
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>示例

下面的示例通过使用 `mutable` 关键字声明 lambda 表达式来解决 C3491：

```
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)