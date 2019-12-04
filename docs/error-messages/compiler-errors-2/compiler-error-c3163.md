---
title: 编译器错误 C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: 436fb112758dfdec9997ff7e6dd7ef8f9dcdc66e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761772"
---
# <a name="compiler-error-c3163"></a>编译器错误 C3163

"构造"：特性与以前的声明不一致

应用于定义的属性与应用于声明的属性冲突。 "%1"

解决 C3163 的一种方法是消除前向声明中的特性。 前向声明中的任何特性都应小于定义上的特性，或在最大程度上等于它们。

C3163 错误的可能原因包括 Microsoft 源代码注释语言（SAL）。 除非使用 **/analyze**标志编译项目，否则 SAL 宏将不会展开。 如果尝试使用/analyze 选项对其进行重新编译，则不使用/analyze 完全编译的程序可能会引发 C3163。 有关 SAL 的详细信息，请参阅[Sal 注释](../../c-runtime-library/sal-annotations.md)。

## <a name="example"></a>示例

下面的示例生成 C3163。

```cpp
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>另请参阅

[SAL 批注](../../c-runtime-library/sal-annotations.md)
