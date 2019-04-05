---
title: 编译器错误 C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: eda3910c99f4c8ea96568f2d475c5d6a1e4cdc7c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041041"
---
# <a name="compiler-error-c3163"></a>编译器错误 C3163

construct： 属性与前面的声明不一致

应用于定义的属性与应用于声明的属性发生冲突。

若要解决 C3163 的一种方法是消除前向声明的属性。 前向声明的任何属性都应小于在定义的属性，或最多等于到它们。

C3163 错误的可能原因包括 Microsoft 源代码注释语言 (SAL)。 除非使用编译你的项目，否则 SAL 宏不展开**分析 /** 标志。 如果你尝试重新编译它与一个程序，而无需完全编译 / 分析可能会引发 C3163 /analyze 选项。 有关 SAL 的详细信息，请参阅[SAL 注释](../../c-runtime-library/sal-annotations.md)。

## <a name="example"></a>示例

下面的示例生成 C3163。

```
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>请参阅

[SAL 批注](../../c-runtime-library/sal-annotations.md)