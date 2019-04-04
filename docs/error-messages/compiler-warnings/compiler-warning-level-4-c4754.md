---
title: 编译器警告（等级 4）C4754
ms.date: 11/04/2016
f1_keywords:
- C4754
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
ms.openlocfilehash: 203f2b97547c7ff8b1d68e3640e62d531b2600e9
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780348"
---
# <a name="compiler-warning-level-4-c4754"></a>编译器警告（等级 4）C4754

比较中的算术运算的转换规则意味着无法执行一个分支。

发出了 C4754 警告，因为比较的结果总是相同。 这可能表示条件的其中一个分支绝不会执行，原因最可能是关联的整数表达式不正确。 此代码缺陷通常在对 64 位体系结构执行了不正确的整数溢出检查时发生。

整数转换规则很复杂，并且有很多微小的缺陷。 作为解决每个 C4754 警告的替代方法，你可以更新代码以使用[SafeInt 库](../../safeint/safeint-library.md)。

## <a name="example"></a>示例

此示例会生成 C4754:

```cpp
// C4754a.cpp
// Compile with: /W4 /c
#include "errno.h"

int sum_overflow(unsigned long a, unsigned long b)
{
   unsigned long long x = a + b; // C4754

   if (x > 0xFFFFFFFF)
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

加法 `a + b` 可能导致在将结果向上转换为 64 位值并分配给 64 位变量 `x` 前发生算术溢出。 这意味着，对 `x` 的检查是多余的，永远不会捕获到溢出。 在这种情况下，编译器将发出以下警告：

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).
```

若要消除此警告，您可以更改赋值语句以将操作数强制转换为 8 字节值：

```cpp
// Casting one operand is sufficient to force all the operands in
// the addition be upcast according to C/C++ conversion rules, but
// casting both is clearer.
unsigned long long x =
   (unsigned long long)a + (unsigned long long)b;
```

## <a name="example"></a>示例

下一个示例也会生成 C4754。

```cpp
// C4754b.cpp
// Compile with: /W4 /c
#include "errno.h"

int wrap_overflow(unsigned long a)
{
   if (a + sizeof(unsigned long) < a) // C4754
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

`sizeof()` 运算符返回了 `size_t`，其大小依赖于体系结构。 该代码示例适用于其中的 `size_t` 是 32 位类型的 32 位体系结构。 然而，在 64 位体系结构中，`size_t` 是 64 位类型。 整数的转换规则意味着，`a` 在表达式 `a + b < a` 中将向上转换 64 位值，就如同采用 `(size_t)a + (size_t)b < (size_t)a` 形式一样。 当 `a` 和 `b` 为 32 位整数时，64 位加法运算永远不会溢出，并且永远不会应用约束。 因此，代码永远不会检测在 64 位体系结构中检测到整数溢出条件。 此示例导致编译器发出以下警告：

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).
```

请注意，警告消息在警告分析遇到违规代码时显式列出了常量值 4 而不是原始的源字符串，`sizeof(unsigned long)` 已转换为常量。 因此，你可能必须追查源代码的哪个表达式与警告消息中的常量值关联。 解析为 C4754 警告消息中的常量的最常见的代码来源是表达式，如 `sizeof(TYPE)` 和 `strlen(szConstantString)`。

在这种情况下，修复后的代码将类似于形式：

```cpp
// Casting the result of sizeof() to unsigned long ensures
// that all the addition operands are 32-bit, so any overflow
// is detected by the check.
if (a + (unsigned long)sizeof(unsigned long) < a)
```

**请注意**编译器警告中引用的行号是语句的最后一行。 在有关分布到多个行的复杂条件语句的警告消息中，具有行代码缺陷的行可能是所报告的行前面几行的行。 例如：

```cpp
unsigned long a;

if (a + sizeof(unsigned long) < a || // incorrect check
    condition1() ||
    a == 0) {    // C4754 warning reported on this line
         // never executes!
         return INVALID_PARAMETER;
}
```